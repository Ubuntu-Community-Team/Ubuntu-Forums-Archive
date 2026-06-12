---
title: "Can't make java work"
date: 2009-06-27
forum: General Help
---

### Post by longbody on 2009-06-27
Hi folks,
I'm trying to use the sun java 6 SDK on Ubuntu 9.04.
I installed it with synaptic and its there on my hard drive.

Then I run:
   sudo update-java-alternatives -l

and it tells me:
   java-6-sun 63 /usr/lib/jvm/java-6-sun
   java-gcj 1042 /usr/lib/jvm/java-gcj

so I run:
   sudo update-java-alternatives -s java-6-sun

and it tells me:
   No alternatives for firefox-javaplugin.so.
   No alternatives for iceape-javaplugin.so.
   No alternatives for iceweasel-javaplugin.so.
   No alternatives for midbrowser-javaplugin.so.
   No alternatives for mozilla-javaplugin.so.
   No alternatives for xulrunner-1.9-javaplugin.so.
   No alternatives for xulrunner-javaplugin.so.
   Using '/usr/lib/jvm/java-6-sun/bin/appletviewer' to provide   'appletviewer'.
   Using '/usr/lib/jvm/java-6-sun/bin/apt' to provide 'apt'.
   Using '/usr/lib/jvm/java-6-sun/bin/extcheck' to provide 'extcheck'.
   Using '/usr/lib/jvm/java-6-sun/bin/HtmlConverter' to provide 'HtmlConverter'.
   Using '/usr/lib/jvm/java-6-sun/bin/idlj' to provide 'idlj'.
   Using '/usr/lib/jvm/java-6-sun/bin/jarsigner' to provide 'jarsigner'.
   Using '/usr/lib/jvm/java-6-sun/bin/jar' to provide 'jar'.
   Using '/usr/lib/jvm/java-6-sun/bin/javac' to provide 'javac'.
   Using '/usr/lib/jvm/java-6-sun/bin/javadoc' to provide 'javadoc'.
   Using '/usr/lib/jvm/java-6-sun/bin/javah' to provide 'javah'.
   Using '/usr/lib/jvm/java-6-sun/bin/javap' to provide 'javap'.
   Using '/usr/lib/jvm/java-6-sun/bin/java-rmi.cgi' to provide 'java- rmi.cgi'.
   Using '/usr/lib/jvm/java-6-sun/bin/jconsole' to provide 'jconsole'.
   Using '/usr/lib/jvm/java-6-sun/bin/jdb' to provide 'jdb'.
   Using '/usr/lib/jvm/java-6-sun/bin/jhat' to provide 'jhat'.
   Using '/usr/lib/jvm/java-6-sun/bin/jinfo' to provide 'jinfo'.
   Using '/usr/lib/jvm/java-6-sun/bin/jmap' to provide 'jmap'.
   Using '/usr/lib/jvm/java-6-sun/bin/jps' to provide 'jps'.
   Using '/usr/lib/jvm/java-6-sun/bin/jrunscript' to provide 'jrunscript'.
   Using '/usr/lib/jvm/java-6-sun/bin/jsadebugd' to provide 'jsadebugd'.
   Using '/usr/lib/jvm/java-6-sun/bin/jstack' to provide 'jstack'.
   Using '/usr/lib/jvm/java-6-sun/bin/jstatd' to provide 'jstatd'.
   Using '/usr/lib/jvm/java-6-sun/bin/jstat' to provide 'jstat'.
   Using '/usr/lib/jvm/java-6-sun/bin/native2ascii' to provide 'native2ascii'.
   Using '/usr/lib/jvm/java-6-sun/bin/rmic' to provide 'rmic'.
   Using '/usr/lib/jvm/java-6-sun/bin/schemagen' to provide 'schemagen'.
   Using '/usr/lib/jvm/java-6-sun/bin/serialver' to provide 'serialver'.
   Using '/usr/lib/jvm/java-6-sun/bin/wsgen' to provide 'wsgen'.
   Using '/usr/lib/jvm/java-6-sun/bin/wsimport' to provide 'wsimport'.
   Using '/usr/lib/jvm/java-6-sun/bin/xjc' to provide 'xjc'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/ControlPanel' to provide 'ControlPanel'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/java' to provide 'java'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/java_vm' to provide 'java_vm'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/javaws' to provide 'javaws'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/jcontrol' to provide 'jcontrol'.
   Using '/usr/lib/jvm/java-6-sun/jre/lib/jexec' to provide 'jexec'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/keytool' to provide 'keytool'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/orbd' to provide 'orbd'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/pack200' to provide 'pack200'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/policytool' to provide  'policytool'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/rmid' to provide 'rmid'.  
   Using '/usr/lib/jvm/java-6-sun/jre/bin/rmiregistry' to provide 'rmiregistry'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/servertool' to provide 'servertool'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/tnameserv' to provide 'tnameserv'.
   Using '/usr/lib/jvm/java-6-sun/jre/bin/unpack200' to provide 'unpack200'.
   No alternatives for firefox-javaplugin.so.
   No alternatives for iceape-javaplugin.so.
   No alternatives for iceweasel-javaplugin.so.
   No alternatives for midbrowser-javaplugin.so.
   No alternatives for mozilla-javaplugin.so.
   No alternatives for xulrunner-1.9-javaplugin.so.
   No alternatives for xulrunner-javaplugin.so.

so I run:
   java -version

and it tells me:
   The program 'java' can be found in the following packages:
    * gij-4.3
    * java-gcj-compat-headless
    * openjdk-6-jre-headless
    * cacao
    * gij-4.2
    * jamvm
    * kaffe
   Try: sudo apt-get install <selected package>
   bash: java: command not found

On the other hand, when I run:
   javac -version

it tells me:
   javac 1.6.0_13

Does anyone have any idea whats happening here ?

---

### Post by QIII on 2009-06-27
It's a bit surprising that you get that when you installed from Synaptic.

It might be worth seeing what happens if you try to do it from the terminal.  You may get told you have the latest versions and nothing will get updated, but give this a whirl:

    sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-fonts
    sudo update-java-alternatives -s java-6-sun

Most likely problem is that you don't have the bin file installed.

(Just so you know, javac is the java compiler.)

---

### Post by barrieluv on 2009-06-27
After you've installed Sun Java 6, you need to make sure your system will use it instead of the one you are currently using.

To set it to use version 6:

```
sudo update-java-alternatives -s java-6-sun
```


And then, to check the system will use the version you have indicated:

```
java -version
```

---

### Post by longbody on 2009-06-27
Hi QIII,

Well, I tried installing from the terminal, it told me the jre and bin were already installed, then it installed the plugin and fonts. update-java-alternatives ran correctly, but java -version still tells me that java is not installed.

So I can still compile java, but not run it.

Only thing I can see is that javac is in the directory:
usr/lib/jvm/java-6-sun/bin
and java is in the directory:
usr/lib/jvm/java-6-sun/jre/bin

executables in the bin directory appear to run correctly, but executables in the jre/bin directory give a 'command not found' message.

This is starting to make my head hurt.

---

### Post by 4835jack on 2009-06-29
Hey

Just had the same problem.
run  sudo apt-get install sun-java6-plugin

Jack

---

