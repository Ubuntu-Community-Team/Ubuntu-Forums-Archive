---
title: "geronimo-jetty7-javaee5-2.2 fails to deploy war application"
date: 2010-05-03
forum: General Help
---

### Post by tapas_mishra on 2010-05-03
I am trying to deploy a helloworld application  of grails in war format which exists.To geronimo web server while deploying it failed and gives following error the username and passwords are the default that come with geromino is it the right way to use or I should do some thing more.GUI based deployment is not possible for me.It is an SSH server where Geromino is running.  
geronimo-jetty7-javaee5-2.2

Any ideas what should I do?  

```

    myserver:~/geronimo-jetty7-javaee5-2.2/bin# ./deploy.sh  deploy /root/a12/target/a12-0.1.war 
        Using GERONIMO_HOME:   /root/geronimo-jetty7-javaee5-2.2
        Using GERONIMO_TMPDIR: var/temp
        Using JRE_HOME:        /root/jdk1.6.0_20/jre
        2010-05-03 05:48:19,158 ERROR [DeployTool] Error: 
        org.apache.geronimo.common.DeploymentException: Operation failed: start of grailsApps/a12/0.1/war failed
            Unknown start exception
            Configuration grailsApps/a12/0.1/war failed to start due to the following reasons:
          The service J2EEApplication=null,WebFilter=charEncodingFilter,WebModule=grailsApps/a12/0.1/war,j2eeType=URLWebFilterMapping,name="[/%5C*]" did not start because grailsApps/a12/0.1/war?J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=WebFilter,name=charEncodingFilter did not start.
          The service J2EEApplication=null,WebFilter=hiddenHttpMethod,WebModule=grailsApps/a12/0.1/war,j2eeType=URLWebFilterMapping,name="[/%5C*]" did not start because grailsApps/a12/0.1/war?J2EEApplication=null,WebFilter=charEncodingFilter,WebModule=grailsApps/a12/0.1/war,j2eeType=URLWebFilterMapping,name=%22[/%5C*]%22 did not start.
          The service J2EEApplication=null,WebFilter=grailsWebRequest,WebModule=grailsApps/a12/0.1/war,j2eeType=URLWebFilterMapping,name="[/%5C*]" did not start because grailsApps/a12/0.1/war?J2EEApplication=null,WebFilter=hiddenHttpMethod,WebModule=grailsApps/a12/0.1/war,j2eeType=URLWebFilterMapping,name=%22[/%5C*]%22 did not start.
          The service J2EEApplication=null,WebFilter=sitemesh,WebModule=grailsApps/a12/0.1/war,j2eeType=URLWebFilterMapping,name="[/%5C*]" did not start because the following dependent services did not start: [grailsApps/a12/0.1/war?J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=WebFilter,name=sitemesh, grailsApps/a12/0.1/war?J2EEApplication=null,WebFilter=grailsWebRequest,WebModule=grailsApps/a12/0.1/war,j2eeType=URLWebFilterMapping,name=%22[/%5C*]%22]
          The service J2EEApplication=null,WebFilter=urlMapping,WebModule=grailsApps/a12/0.1/war,j2eeType=URLWebFilterMapping,name="[/%5C*]" did not start because the following dependent services did not start: [grailsApps/a12/0.1/war?J2EEApplication=null,WebFilter=sitemesh,WebModule=grailsApps/a12/0.1/war,j2eeType=URLWebFilterMapping,name=%22[/%5C*]%22, grailsApps/a12/0.1/war?J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=WebFilter,name=urlMapping]
          The service J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=WebFilter,name=sitemesh did not start because Could not initialize DecoratorMapper : org.codehaus.groovy.grails.web.sitemesh.GrailsLayoutDecoratorMapper: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'grailsApplication' defined in ServletContext resource [/WEB-INF/applicationContext.xml]: Invocation of init method failed; nested exception is java.lang.NoSuchMethodError: org.codehaus.groovy.runtime.GroovyCategorySupport.getCategoryNameUsage(Ljava/lang/String;)Ljava/util/concurrent/atomic/AtomicInteger;
          The service J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=WebFilter,name=charEncodingFilter did not start because Error creating bean with name 'grailsApplication' defined in ServletContext resource [/WEB-INF/applicationContext.xml]: Invocation of init method failed; nested exception is java.lang.NoSuchMethodError: org.codehaus.groovy.runtime.GroovyCategorySupport.getCategoryNameUsage(Ljava/lang/String;)Ljava/util/concurrent/atomic/AtomicInteger;
          The service J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=WebFilter,name=urlMapping did not start because Error creating bean with name 'grailsApplication' defined in ServletContext resource [/WEB-INF/applicationContext.xml]: Invocation of init method failed; nested exception is java.lang.NoSuchMethodError: org.codehaus.groovy.runtime.GroovyCategorySupport.getCategoryNameUsage(Ljava/lang/String;)Ljava/util/concurrent/atomic/AtomicInteger;
          The service J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=Servlet,name=default did not start because com.opensymphony.module.sitemesh.factory.FactoryException: Could not initialize DecoratorMapper : org.codehaus.groovy.grails.web.sitemesh.GrailsLayoutDecoratorMapper: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'grailsApplication' defined in ServletContext resource [/WEB-INF/applicationContext.xml]: Invocation of init method failed; nested exception is java.lang.NoSuchMethodError: org.codehaus.groovy.runtime.GroovyCategorySupport.getCategoryNameUsage(Ljava/lang/String;)Ljava/util/concurrent/atomic/AtomicInteger;
          The service J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=Servlet,name=grails did not start because com.opensymphony.module.sitemesh.factory.FactoryException: Could not initialize DecoratorMapper : org.codehaus.groovy.grails.web.sitemesh.GrailsLayoutDecoratorMapper: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'grailsApplication' defined in ServletContext resource [/WEB-INF/applicationContext.xml]: Invocation of init method failed; nested exception is java.lang.NoSuchMethodError: org.codehaus.groovy.runtime.GroovyCategorySupport.getCategoryNameUsage(Ljava/lang/String;)Ljava/util/concurrent/atomic/AtomicInteger;
          The service J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=Servlet,name=grails-errorhandler did not start because grailsApps/a12/0.1/war?J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=Servlet,name=grails did not start.
          The service J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=Servlet,name=gsp did not start because grailsApps/a12/0.1/war?J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=Servlet,name=grails-errorhandler did not start.
          The service J2EEApplication=null,WebModule=grailsApps/a12/0.1/war,j2eeType=Servlet,name=jsp did not start because com.opensymphony.module.sitemesh.factory.FactoryException: Could not initialize DecoratorMapper : org.codehaus.groovy.grails.web.sitemesh.GrailsLayoutDecoratorMapper: org.springframework.beans.factory.BeanCreationException: Error creating bean with name 'grailsApplication' defined in ServletContext resource [/WEB-INF/applicationContext.xml]: Invocation of init method failed; nested exception is java.lang.NoSuchMethodError: org.codehaus.groovy.runtime.GroovyCategorySupport.getCategoryNameUsage(Ljava/lang/String;)Ljava/util/concurrent/atomic/AtomicInteger;
        
        
            at org.apache.geronimo.deployment.cli.CommandDistribute.executeOnline(CommandDistribute.java:169)
            at org.apache.geronimo.deployment.cli.CommandDistribute.execute(CommandDistribute.java:125)
            at org.apache.geronimo.deployment.cli.DeployTool.execute(DeployTool.java:168)
            at org.apache.geronimo.kernel.util.MainConfigurationBootstrapper.main(MainConfigurationBootstrapper.java:45)
            at org.apache.geronimo.cli.AbstractCLI.executeMain(AbstractCLI.java:65)
            at org.apache.geronimo.cli.deployer.DeployerCLI.main(DeployerCLI.java:31)

```

---

### Post by dino99 on 2010-05-03
debug it sep by step, better help on programming forum

---

### Post by tapas_mishra on 2010-05-03
Ok I shall post it there or is there any way to move this thread there?

---

