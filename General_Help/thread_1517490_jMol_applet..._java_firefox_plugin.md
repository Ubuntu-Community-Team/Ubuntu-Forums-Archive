---
title: "jMol applet... java firefox plugin"
date: 2010-06-25
forum: General Help
---

### Post by jfmxl on 2010-06-25
I am trying to view jMol models via firefox but they don't show up. I assume that's due to the IcedTea java plugin. I cannot get firefox to use the sun java plugin.

[INDENT]Distributor ID:	Ubuntu
Description:	Ubuntu 10.04 LTS
Release:	10.04
Codename:	lucid

jfl@ws3:~$ uname -a
Linux ws3 2.6.32-22-generic #36-Ubuntu SMP Thu Jun 3 19:31:57 UTC 2010 x86_64 GNU/Linux

Mozilla/5.0 (X11; U; Linux x86_64; th-TH; rv:1.9.2.3) Gecko/20100423 Ubuntu/10.04 (lucid) Firefox/3.6.3

java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) 64-Bit Server VM (build 16.3-b01, mixed mode)
[/INDENT]

I tried symlinks :

[INDENT]jfl@ws3:/usr/lib$ ls -l firefox*/plugins
lrwxrwxrwx 1 root root   25 2010-06-07 20:24 firefox-3.6.3/plugins -> ../firefox-addons/plugins

firefox-addons/plugins:
total 4
lrwxrwxrwx 1 root root 67 2010-06-07 18:59 libjavaplugin_jni.so -> /usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/libjavaplugin_jni.so

firefox/plugins:
total 0
lrwxrwxrwx 1 root root 52 2010-06-25 14:53 libjavaplugin_jni.so -> /usr/lib/firefox-addons/plugins/libjavaplugin_jni.so
[/INDENT]
and I added a link to 

[INDENT]jfl@ws3:~$ ls -l .mozilla/plugins/
total 9368
lrwxrwxrwx 1 jfl jfl      67 2010-06-25 15:16 libjavaplugin_jni.so -> /usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/libjavaplugin_jni.so

[/INDENT]Still no joy.

The about:plugins page in firefox shows :


[INDENT]IcedTea NPR Web Browser Plugin (using IcedTea6 1.8 (6b18-1.8-0ubuntu1))

    File: /usr/lib/jvm/java-6-openjdk/jre/lib/amd64/IcedTeaPlugin.so
    Version: 
    The IcedTea NPR Web Browser Plugin (using IcedTea6 1.8 (6b18-1.8-0ubuntu1)) executes Java applets.

MIME Type 	Description 	Suffixes 	Enabled
application/x-java-vm 	IcedTea 	class,jar 	Yes
application/x-java-applet 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-applet;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-applet;jpi-version=1.6.0_18 	IcedTea 	class,jar 	Yes
application/x-java-bean 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.2.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.3.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.1 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.4.2 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.5 	IcedTea 	class,jar 	Yes
application/x-java-bean;version=1.6 	IcedTea 	class,jar 	Yes
application/x-java-bean;jpi-version=1.6.0_18 	IcedTea 	class,jar 	Yes
[/INDENT]
I'd really like to be able to use the jMol applets via firefox.

Any help appreciated greatly.

Thanks

---

### Post by jfmxl on 2010-06-26
After  I received no answers here I cross-posted to the mozilla forum and was answered quite quickly...

[INDENT]Does /usr/lib/jvm/java-6-sun-1.6.0.20/jre/lib/amd64/libnpjp2.so exist? You should be linking against that. That is the new Java plugin. The old Java plugin is no longer supported.

You also need to make sure that the IcedTea plugin is not being detected by Firefox.[/INDENT]

I tried that...

[INDENT]I did have the new java-sun plugin on board. I did change the links to point to it. When I then viewed about:plugins I found the new plugin to be operative. I can now view jMol applets and am a happy man. Thank you very much.[/INDENT]

---

