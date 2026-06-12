---
title: "Cannot compile OpenACN"
date: 2010-03-18
forum: General Help
---

### Post by Hund on 2010-03-18
I cant compile OpenACN on Debian Squeeze, I've followed this guide: [http://pierky.wordpress.com/2009/02/07/installing-tr-069-openacs-on-a-fresh-debian-setup/](http://pierky.wordpress.com/2009/02/07/installing-tr-069-openacs-on-a-fresh-debian-setup/)

When I'm trying to build OpenACS with the command "ant" it results in this:

```
    [...]
        [javac] location: class org.openacs.utils.Jms
        [javac]     private QueueSession queuesession;
        [javac]             ^
        [javac] /home/johan/openacs/acs-ejb/src/java/org/openacs/utils/Jms.java:35: package javax.jms does not exist
        [javac]     private javax.jms.Queue queue;
        [javac]                      ^
        [javac] /home/johan/openacs/acs-ejb/src/java/org/openacs/utils/Jms.java:36: cannot find symbol
        [javac] symbol  : class QueueConnection
        [javac] location: class org.openacs.utils.Jms
        [javac]     private QueueConnection conn;
        [javac]             ^
        [javac] /home/johan/openacs/acs-ejb/src/java/org/openacs/utils/Jms.java:39: cannot find symbol
        [javac] symbol  : class JMSException
        [javac] location: class org.openacs.utils.Jms
        [javac]     public Jms() throws NamingException, JMSException {
        [javac]                                          ^
        [javac] /home/johan/openacs/acs-ejb/src/java/org/openacs/utils/Jms.java:59: cannot find symbol
        [javac] symbol  : class JMSExceptionRun ant to build OpenACS

    ant
    ] required: java.util.Iterator<org.openacs.SoftwareLocal>
        [javac]                 Iterator<SoftwareLocal> itSoftware = sh.findByHardware(host.getHwid()).iterator();
        [javac]                                                                                                ^
        [javac] Note: Some input files use or override a deprecated API.
        [javac] Note: Recompile with -Xlint:deprecation for details.
        [javac] 100 errors
        [javac] 36 warnings

        [javac] location: class org.openacs.utils.Jms
        [javac]     public void setupJMS() throws NamingException, JMSException {
        [javac]                                                    ^
        [javac] /home/johan/openacs/acs-ejb/src/java/org/openacs/Configurator.java:436: warning: [unchecked] unchecked conversion
        [javac] found   : java.util.Iterator
        [javac] required: java.util.Iterator<org.openacs.SoftwareLocal>
        [javac]                 Iterator<SoftwareLocal> itSoftware = sh.findByHardware(host.getHwid()).iterator();
        [javac]                                                                                                ^
        [javac] Note: Some input files use or override a deprecated API.
        [javac] Note: Recompile with -Xlint:deprecation for details.
        [javac] 100 errors
        [javac] 36 warnings
```

---

### Post by au3 on 2010-04-10
you must install jboss-4.2.3 from zip from sourceforge and edit build.properties in openacs source dir. jboss that is installed as package in ubuntu is unfunctional.

---

