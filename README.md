# Spring Version Management

If you've ever created a moderately complex project which uses Spring, you've
likely come across issues having to manage versions of Spring transitive
dependencies.

Your project uses Spring 3.2.5.RELEASE, but something else you're depending on
imports some otherwise unused Spring module, at 3.0.7. I'm looking at you,
Spring Security.

You end up declaring a `dependencyManagement` entry for just about every Spring
module there is, to ensure that anything you bring in uses the correct version.

Enter `spring-version`

```xml
<project>
  <dependencyManagement>
    <dependencies>
      <dependency>
        <groupId>com.github.ptomli.spring-version</groupId>
        <artifactId>spring-version</artifactId>
        <version>3.2.5.RELEASE</version>
        <type>pom</type>
        <scope>import</scope>
      </dependency>
    </dependencies>
  </dependencyManagement>
</project>
```

`spring-version` simply declares a `dependencyManagement` entry for each Spring
module, at its own `project.version`. So, `spring-version` `3.2.5.RELEASE`
will result in any Spring transitive dependency being imported at
`3.2.5.RELEASE`. Done, finished and klaar!

There are companion projects to handle other SpringSource project versions, such
as
[spring-integration-version](https://github.com/ptomli/spring-integration-version)
and
[spring-security-version](https://github.com/ptomli/spring-security-version)
