#set( $symbol_pound = '#' )
#set( $symbol_dollar = '$' )
#set( $symbol_escape = '\' )
This project is built using Eclipse Tycho (https://www.eclipse.org/tycho/) and requires at least maven 3.0 (http://maven.apache.org/download.html) to be built via CLI. 
Simply run :

    mvn install

The first run will take quite a while since maven will download all the required dependencies in order to build everything.

In order to use the generated eclipse plugins in Eclipse, you will need m2e (https://www.eclipse.org/m2e) 
and the m2eclipse-tycho plugin (https://github.com/tesla/m2eclipse-tycho/). Update sites to install these plugins : 

* m2e stable update site : https://download.eclipse.org/technology/m2e/releases/
* m2eclipse-tycho dev update site : http://repo1.maven.org/maven2/.m2e/connectors/m2eclipse-tycho/0.7.0/N/0.7.0.201309291400/

#if ($signing_support == "true" || $signing_support == "y" || $signing_support == "yes" )

Signed artifacts will be created when the `sign` profile is used.

    mvn package -Psign

In order to sign artifacts, you will need to generate/provide a keystore first (see http://docs.oracle.com/javase/6/docs/technotes/tools/solaris/jarsigner.html) and configure your settings.xml like :

```
  <profiles>
    <profile>
    <id>sign</id>
      <properties>
        <sign.keystore>~/.ssh/sample.keystore</sign.keystore>
        <sign.alias>sample</sign.alias>
        <sign.storepass>samplepass</sign.storepass>
        <sign.keypass>samplepass</sign.keypass>
      </properties>
    </profile>
  </profiles>
```
#end
