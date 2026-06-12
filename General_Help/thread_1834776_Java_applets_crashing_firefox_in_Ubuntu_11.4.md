---
title: "Java applets crashing firefox in Ubuntu 11.4"
date: 2011-08-28
forum: General Help
---

### Post by biju1982.k20 on 2011-08-28
Hi,

I am new to Ubuntu forum. Recently installed Ubuntu 11.4 in my Dell Inspiron 1525 laptop. Everything is working fine except our ERP application , which runs on Java plugin. Have tried install Sun-Java-Plugin and its not running, where as its working with OpenJDK and Icedtea Plugin. But the issue is when we try to run report from the application it crashes firefox. Even we tried the same with Chromium and its giving error as icedtea plugin crash. I am IT manager and would like to install ubuntu in other systems as we. For us main thing is ERP application should run. Please help someone.

Regards,
Biju Kunjumon

---

### Post by YesWeCan on 2011-08-28
You might want to uninstall the open source stuff and download the latest Java from Oracle.

---

### Post by biju1982.k20 on 2011-08-28
Thanks for your reply. We have tried removing openjdk, icedtea plugin and installed Sun-Java6-JRe, JDK, Fonts, Source and Sun-Java-Plugin. After installing sun java, our ERP application not starting applets at all. We tried the same application in Fedora 9 and our ERP was working fine on it. Please help someone , else i have to go back to try with Fedora versions.

Thanks,
Biju

---

### Post by 1clue on 2011-08-28
Don't try to outsmart the JVM.

Once you get both JVMs installed, you need to select which one you want.

$sudo update-alternatives --config java
[sudo] password for ken: 
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
* 2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number: 2

$java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)

---

### Post by 1clue on 2011-08-28
What you use for your ERP on your server may be a different approach to what you use on clients.

We use a hand-installed binary from Oracle for the server, because we don't want any inadvertent upgrades to mess up the installation.

I generally set it up like this, assuming you are root:

mkdir -p /opt/sun-jdk
cd /opt/sun-jdk
tar -xzf /path/to/sunjdk-zip.tgz
ln -s jdk1.6.xx.yy current

and then my JAVA_HOME is set to /opt/sun-jdk/current.  If I'm going that route, avoid confusion and don't even have Ubuntu's sun-jdk on there at all.


On the clients, you probably want everything to update as updates become available, so you need to work with the rather non-standard way that Linux distributions tend to install the JRE and plugin.

---

### Post by biju1982.k20 on 2011-08-29
Thanks for your reply. We have tried making Sun-Java as default and the version shows as below,

biju@biju-Inspiron-1525:~$ sudo update-alternatives --config java
[sudo] password for biju: 
There are 2 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
  0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
* 1            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  2            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice
[*], or type selection number: 2
update-alternatives: using /usr/lib/jvm/java-6-sun/jre/bin/java to provide /usr/bin/java (java) in manual mode.
biju@biju-Inspiron-1525:~$ java -version
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) Server VM (build 20.1-b02, mixed mode)
biju@biju-Inspiron-1525:~$ 

But still firefox getting crash on running the report from Java. Please find below the crash report,

Add-ons: [email]langpack-en-ZA@firefox.mozilla.org:6.0,langpack-en-GB@firefox.mozilla.org:6.0,ubufox@ubuntu.com[/email]:0.9.1,{972ce4c6-7e08-4474-a285-3208198ce6fd}:6.0
BuildID: 20110812234425
CrashTime: 1314605266
EMCheckCompatibility: true
Email:
FramePoisonBase: 00000000f0dea000
FramePoisonSize: 4096
InstallTime: 1314356405
Notes: OpenGL: Tungsten Graphics, Inc -- Mesa DRI Intel(R) 965GM GEM 20100330 DEVELOPMENT x86/MMX/SSE2 -- 2.1 Mesa 7.10.2

ProductName: Firefox
ReleaseChannel: release
SecondsSinceLastCrash: 245
StartupTime: 1314605064
Theme: classic/1.0
Throttleable: 1
URL: [http://192.168.0.6:13000/](http://192.168.0.6:13000/)
Vendor: Mozilla
Version: 6.0

This report also contains technical information about the state of the application when it crashed.

---

### Post by 1clue on 2011-08-31
Is there a stack trace on your java console, or something reported in your ERP server log?

If you have a sizeable applet you could need to adjust your memory settings on the applet side.

---

### Post by biju1982.k20 on 2011-09-01
The same ERP is working fine and the report also generating when i tried installing Ubuntu 8.04 with Java 5.
But its not working with Ubuntu 11.04 with Java 6. Is there any way i can downgrade the Java from 6 to 5 including plugin.

---

### Post by 1clue on 2011-09-01
So there's no java console?  Can't figure out what the problem is if there's no stack trace.

Yes, you can downgrade by going into Synaptic and searching for the proper version, but so far we haven't even seen what the problem is yet.

Have you verified that the ERP system works with a Windows Firefox with Java 6?  If so it should work in Linux as well.

My company uses a large Java applet for A/R software, and we need to tweak each client.

---

### Post by biju1982.k20 on 2011-09-15
Dear All,
 
Thanks for your replies. We have tried a lot for a solution to run report from our ERP in Ubuntu 11.04 but didnt work bez of icedtea plugin crash and also same in Sun Java Plugin. Installed Ubuntu 10.10 and everything is working fine. Hope in the next relase of Ubuntu this crash issue will be solved.
 
Regards,
Biju

---

