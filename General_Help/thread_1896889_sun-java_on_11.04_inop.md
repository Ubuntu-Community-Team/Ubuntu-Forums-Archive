---
title: "sun-java on 11.04 inop?"
date: 2011-12-18
forum: General Help
---

### Post by ottosykora on 2011-12-18
Can someone tell me what it is about exactly?

I have on my 11.04 sun-java installed, however it seems not to work at all. Any java seems to be taken over by the open java.

I wanted use the sun-java for special app needing it for crypto things, but this seems not possible.

When I uninstall all open java, no java works any more.

I managed even to give the sun-java plugin to the firefox, when diasabling the openjava plugin, firefox crashes completely when needing to call for java.

Is there no more way to use sun-java at all?

---

### Post by ottosykora on 2011-12-18
can someone tell what file name is the sun-java plugin for the firefox 8 under x64 ?

---

### Post by ottosykora on 2011-12-18
I could make sun-java the defaoult java now, version gives back:

```
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)
otto@LAPTOPOTTOS6:~$ 
```


I managed to find and copy the pluging to firefox8 plugin folder and it now appears under plugin gui.

However all java tasks in firefox are still connected to iced tea and when going to java.com to test version, it tellsme it is version 22 , which is the one of the open java.

If I disable the iced tea, firefox crashes , it does not want to use the sun-java plugin at all, thought it is installed and listed.

How to make also in FF the sun-java work?

---

### Post by BC59 on 2011-12-18
According to WebUpd8 you have to uninstall manually all old java plugins after the installation of Oracle Java.

[http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html](http://www.webupd8.org/2011/09/how-to-install-oracle-java-7-jdk-in.html)

---

### Post by CaptinGoogle on 2011-12-20
Sorry boys looks like regular java is leaving. So if you want to install you have to go to their website. [http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/](http://www.omgubuntu.co.uk/2011/12/java-to-be-removed-from-ubuntu-uninstalled-from-user-machines/)

---

### Post by newbie2 on 2011-12-22
> Java To Stay In Ubuntu

Java is not being removed from Ubuntu. OpenJDK is the open source version Java, is developed primarily by Oracle, is becoming the reference implementation and is available in Ubuntu. The Sun-Java packages under the DLJ were a temporary stop-gap we put in place before Java was liberated as GPL. Removing these packages is just housekeeping. There are some programs in the Ubuntu repository that will need to do rework on their dependencies (Minecraft in particular), but this is an entirely expected lifecycle step and actually I'm surprised it's not happened before.

Nothing to see here folks, move along. 
[http://blogs.computerworlduk.com/simon-says/2011/12/why-java-isnt-dead-on-ubuntu/index.htm](http://blogs.computerworlduk.com/simon-says/2011/12/why-java-isnt-dead-on-ubuntu/index.htm)

---

### Post by PikeHill on 2011-12-23
There might not be anything to see, but I've got something to say & I'm not moving anywhere.

Please return sun-java6-plugin to the repository. I am rebuilding after a  HD crash and IcedTea plugins DO NOT WORK. The problem: sites freeze or crash when loading applets. This problem was previously  solved by removing OpenJRE and replacing it with a clean Oracle/Sun version  and removing IcedTea and replacing it with sun-java6-plugin.  Unfortunately the plugin has been moved and downloads are now very  difficult to find.

A few months ago, while I was first trying to solve my Java problems, I talked with a few site developers who said, point blank, they  use Sun(Oracle) Java and will not support anyone using other versions.

Now that the packages have been 'cleaned', how do I get rid of OpenJDK and IcedTea and replace them with something that works?

I am using Ubuntu 11.10 and Firefox 8.0

---

### Post by sammiev on 2011-12-23
Manually install [JRE Java]("http://sites.google.com/site/easylinuxtipsproject/java"). :)

---

### Post by QIII on 2011-12-23
> **sammiev said:**
> Manually install [JRE Java]("http://sites.google.com/site/easylinuxtipsproject/java"). :)

This.

Please first uninstall any Sun Java you may have installed currently first.  If you got it from the repos, it is update 26 and is old, unsecure and buggy anyway.

Sun Java will not be returning to the repos.  It's probably as simple as that.  Despite the fact that OpenJDK is a fine effort to open source Java, much of the world still does not see it as Java.  My clients, for instance.

This shall (hopefully) pass.

---

### Post by sammiev on 2011-12-23
> **QIII said:**
> This.

Please first uninstall any Sun Java you may have installed currently first.  If you got it from the repos, it is update 26 and is old, unsecure and buggy anyway.

Sun Java will not be returning to the repos.  It's probably as simple as that.  Despite the fact that OpenJDK is a fine effort to open source Java, much of the world still does not see it as Java.  My clients, for instance.

This shall (hopefully) pass.

The post I added has it all built in. :)

---

### Post by QIII on 2011-12-23
Which is why I said, "This". :P

I was in contact with one of the maintainers of that tutorial the other day to be made happy by finding out that something I had been unhappy about in the instructions had been removed.

---

