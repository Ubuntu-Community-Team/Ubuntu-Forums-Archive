---
title: "How do i install Open Laszlo(9.10)"
date: 2009-12-14
forum: General Help
---

### Post by JoeyF on 2009-12-14
I have the tar.gz, But what do now?

I tried it on Vista but it said i needed the Java JDK but i couldn't figure out how to do it.

How would i do it on Ubuntu?


Heres the Linux Instructions:
```

Unix/Linux

    * Download the OpenLaszlo Server for Unix/Linux.
    * Use tar zxvf to unzip and untar the distribution from /usr/local (or wherever you want it to go; you can even use your home directory for safety).
    * For SWF9 development on Unix, you will need to manually chmod 755 all the binaries in WEB-INF/server/bin/ before you can compile. This is true for both the .war and .gz distributions.
    * DON'T just copy the Tomcat folder into /usr/local. Keep the whole distribution together. So if you put it in /usr/local, it would look something like this:
    * /usr/local/lps-4.6.1/     ...with Server/tomcat-5.0.24 as a subdirectory of lps-4.6.1
    * Make sure that JAVA_HOME is set correctly. If the instructions below don't work, see the instructions that come with the Java SDK.
    * You can check which version of java you have by typing:
        $ echo $JAVA_HOME
        and you should see something like:
        /usr/java/j2sdk1.4.0
        if not, type:
        which java to find Java on your machine. If no value is returned check installation of Java.
        Export JAVA_HOME by typing:
        export JAVA_HOME=(location of Java on your machine)
    * and you should see something like:
          /usr/java/j2sdk1.4.0
    * Make sure that you have the version 5 or greater of the Macromedia Flash browser plugin installed.
    * Finally run the
          /lps-3.3/Server/tomcat-5.0.24/bin/startup.sh
        script, and you're ready to go. This script will set the following environment variables:
        CATALINA_BASE
        CATALINA_HOME
        CATALINA_TMDIR
        JAVA_HOME - note that JAVA_HOME must be set before running the script
    * Now test your installation.
    * http://www.laszlosystems.com/lps-3.3/docs/installation/run.html
    * Link to hello.lzx brings you to http://localhost:8080/lps-3.3/examples/hello.lzx

Linux Notes

On some installations of RedHat 7.2 Linux, you may need the XFree86-libs RPM from
    http://updates.redhat.com/7.2/en/os/i386/.

In order to access JSP pages, you may need to copy $JAVA_HOME/jre/lib/tools.jar to lps-4.6.1/Server/tomcat-5.0.24/common/lib. 
```

I'm currently learning Python and am a noob programmer but plan on using OL soon.

I didn't understand a word of:
 
* For SWF9 development on Unix, you will need to manually chmod 755 all the binaries in WEB-INF/server/bin/ before you can compile. This is true for both the .war and .gz distributions.

Can you noob that down for me?


Thanks.
:D

---

### Post by smokinblues on 2010-02-17
I'm running Jaunty, and this is how I installed OpenLazslo.
I will try it on Karmic tonight and post if there is a difference.

1. sudo apt-get install sun-java6-jdk
2. sudo update-java-alternatives -s java-6-sun
3. sudo su -
4. export JAVA_HOME=/usr/lib/jvm/java-6-sun/
5. cd /usr/local
6.  wget [http://download.openlaszlo.org/4.7.1/openlaszlo-4.7.1-unix.tar.gz](http://download.openlaszlo.org/4.7.1/openlaszlo-4.7.1-unix.tar.gz)
7. tar xvzf openlaszlo-4.7.1-unix.tar.gz
8. /usr/local/lps-4.7.0/Server/tomcat-5.0.24/bin/startup.sh

you should get :
Using CATALINA_BASE: /usr/local/lps-4.7.0/Server/tomcat-5.0.24
Using CATALINA_HOME: /usr/local/lps-4.7.0/Server/tomcat-5.0.24
Using CATALINA_TMPDIR: /usr/local/lps-4.7.0/Server/tomcat-5.0.24/temp
Using JAVA_HOME: /usr/lib/jvm/java-6-sun/

I hope that helps. The key to the JAVA_HOME problem for me was the "sudo update-java-alternatives -s java-6-sun" line.

---

### Post by vnt87 on 2010-03-02
> **smokinblues said:**
> 
I hope that helps. The key to the JAVA_HOME problem for me was the "sudo update-java-alternatives -s java-6-sun" line.

I did that but still got the dreaded "The JAVA_HOME environment variable is not defined" error. Any idea?
Is the "sudo update-java-alternatives -s java-6-sun" supposed to output any message? It didn't display any message on my machine, it simply returns to the command prompt.

---

### Post by bhartman35 on 2010-05-02
Hi.

I'd like to piggy-back on this, if I might.  I'm getting the following error when I try to run lzc, after following the instructions here.


```
localhost/lps-4.7.2/WEB-INF/lps/server/bin/lzenv: No such file or directory
Exception in thread "main" java.lang.NoClassDefFoundError: org/openlaszlo/compiler/Main
Caused by: java.lang.ClassNotFoundException: org.openlaszlo.compiler.Main
	at java.net.URLClassLoader$1.run(URLClassLoader.java:202)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:190)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:301)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:248)
Could not find the main class: org.openlaszlo.compiler.Main.  Program will exit.

```

Any help would be greatly appreciated.  Thanks. :)

---

### Post by benj.545 on 2010-10-21
i cant install the java thingy and that's the first step, any help?

---

