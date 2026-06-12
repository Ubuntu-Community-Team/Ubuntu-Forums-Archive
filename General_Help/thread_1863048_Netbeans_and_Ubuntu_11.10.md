---
title: "Netbeans and Ubuntu 11.10"
date: 2011-10-17
forum: General Help
---

### Post by praxis1949 on 2011-10-17
Hi,

I just upgraded from (I think) Ubuntu 11,04 to 11.1. After the upgrade, I could not find my previous version of Netbeans. I then uninstalled what was there, and tried to reinstall Netbeans EXCEPT I can't find the Netbeans package. I tried the "sudo apt-get install netbeans" approach in the terminal, and received the reply "unable to locate package netbeans".

What gives? Should I install the Linux version from the "Netbeans" web site?

Regards


John S
Aylmer, Quebec Canada

---

### Post by Madeentje on 2011-10-17
I have the same problem...

What happened to the repositories for NetBeans, in Ubuntu 11.10? In 11.04 we had 6.9 (even though NetBeans 7 had been released quite a while ago already).
I know I can install it through the installer on the website, but I highly prefer to install my programs via the repositories, even if they are a bit outdated.
I've been waiting for this for a couple of days now already, hoping they forgot to add it to the repositories, or are working on it... Is NetBeans maybe be abandoned by the official Ubuntu repositories (I read something about this somewhere)?

I'm surprised no more questions arise about this issue. I suppose NetBeans is widely used...
Can someone please clarify what's going on? I really need NetBeans soon...

Greets,
Madeentje

---

### Post by Gyokuro on 2011-10-17
Hi,

what does:

sudo apt-cache search netbeans

deliver? Ok - it's a bug look here ([https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/822753](https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/822753))

I'm a netbeans user too but I download it always and install it in my ~/pwd/Tools directory :-)

---

### Post by Madeentje on 2011-10-17
> **Gyokuro said:**
> Hi,

what does:

sudo apt-cache search netbeans

deliver? Ok - it's a bug look here ([https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/822753](https://bugs.launchpad.net/ubuntu/+source/netbeans/+bug/822753))

I'm a netbeans user too but I download it always and install it in my ~/pwd/Tools directory :-)

When I enter that command I get this output:

```
gcj-4.4-source - GCJ java sources for use in IDEs like eclipse and netbeans
gcj-4.5-source - GCJ java sources for use in IDEs like eclipse and netbeans
gcj-4.6-source - GCJ java sources for use in IDEs like eclipse and netbeans
libbeansbinding-java - Beans Binding API
libbeansbinding-java-doc - Beans Binding API
libnb-javaparser-java - Parser for the Java language which is good for use in tools
libnb-platform-devel-java - Build harness for NetBeans Platform
libnb-platform12-java - NetBeans Platform for building rich desktop applications in Java
libnb-platform12-java-doc - NetBeans Platform javadoc
libnetbeans-cvsclient-java - NetBeans CVS Client library
libopenide-util-java - OpenIde utility library
libsezpoz-java - Lightweight library for modular service lookups
libsezpoz-java-doc - Documentation for SezPoz
libswing-layout-java - Extensions to Swing layout
libswing-layout-java-doc - Extensions to Swing layout - contains Javadoc API documentation
python-envisage - Extensible Application Framework
python-envisagecore - Extensible Application Framework

```

And yes, I also saw that "post" on launchpad, but not sure what it means... To be honest I'm not very familiar with Launchpad, I'm a fairly new Linux-user... Only using it for ~2 months now.

---

### Post by Gyokuro on 2011-10-17
> **Madeentje said:**
> When I enter that command I get this output:

```
gcj-4.4-source - GCJ java sources for use in IDEs like eclipse and netbeans
gcj-4.5-source - GCJ java sources for use in IDEs like eclipse and netbeans
gcj-4.6-source - GCJ java sources for use in IDEs like eclipse and netbeans
libbeansbinding-java - Beans Binding API
libbeansbinding-java-doc - Beans Binding API
libnb-javaparser-java - Parser for the Java language which is good for use in tools
libnb-platform-devel-java - Build harness for NetBeans Platform
libnb-platform12-java - NetBeans Platform for building rich desktop applications in Java
libnb-platform12-java-doc - NetBeans Platform javadoc
libnetbeans-cvsclient-java - NetBeans CVS Client library
libopenide-util-java - OpenIde utility library
libsezpoz-java - Lightweight library for modular service lookups
libsezpoz-java-doc - Documentation for SezPoz
libswing-layout-java - Extensions to Swing layout
libswing-layout-java-doc - Extensions to Swing layout - contains Javadoc API documentation
python-envisage - Extensible Application Framework
python-envisagecore - Extensible Application Framework

```

And yes, I also saw that "post" on launchpad, but not sure what it means... To be honest I'm not very familiar with Launchpad, I'm a fairly new Linux-user... Only using it for ~2 months now.

No problem - I assume you are a java dev so you have to install at first the jdk (you need it anyways) and afterwards download netbeans from netbeans.org. 

Netbeans install you via:

sh ./netbeans-7.0.1*.sh

or you can make it executable

chmod +x netbeans*.sh
./netbeans*.sh

and the rest should be easy. Happy coding!

---

### Post by Madeentje on 2011-10-17
Thanks for the quick clarification, although I already knew that.

What I'm looking for is an explanation as to why there's no NetBeans in the Ubuntu 11.10 repositories anymore... Because as you can read in my first post (2nd post in this thread) I really prefer to install my programs that way instead of manually installing them. As a last resort I guess I'll have to do it manually.

I've been googling for a while and oddly enough there's no clear reason for why it's been removed from the repositories.

Again thanks for your quick replies :).

---

### Post by praxis1949 on 2011-10-18
Aha! Well, downloading fron Netbeans, and then installing via the documentation on the Ubuntu site (help.ubuntu.com/community/netbeans) is painless (and I believe the  installation of the JDK is automatic).

John Smith
Aylmer, Quebec Canada

---

### Post by Madeentje on 2011-10-21
Bump? Is there any news on this subject? Will we see NetBeans in the Ubuntu repositories again, or has it been removed permanently... And if so, why?

---

### Post by critin on 2011-10-25
According to: [http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/]("http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/")

Scroll down to** Special Note:**

<<<*Avidemux, Netbeans, and Quanta are not available in the 11.10 repositories. They are still available in previous releases of Ubuntu.*>>

---

### Post by Madeentje on 2011-10-25
Hmm... So impossible to install those programs through the repositories in 11.10? Or is it possible to install programs on 11.10 from the previous repositories too? I've already installed NetBeans manually now, although I'm wondering what's behind the decision to remove NetBeans from the repos (or if they plan to still add it).

---

### Post by AkifTariq on 2011-10-25
I also cannot find the explanation of why Netbeans has been removed from the 11.10 repos. There are a few more packages which I am not able to install. The transition from 11.04 to 11.10 has been pain full for me. None of the previous Ubuntu upgrades have been pain full.

The worst is that I do not find any statement from Ubuntu, and its future plans for including such packages.

I tried installing Netbeans from the netbeans.org installer, but it demands for JDK and it is also not included in the repos. What a shame!

---

### Post by muhdazmilug on 2011-10-27
to install java jdk, 
```
sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

---

### Post by alco75 on 2011-10-27
You don't need the Sun JRE to run NetBeans.
The Open JRE works fine.

```

ii  openjdk-6-jre                          6b23~pre10-0ubuntu5                     OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre-headless                 6b23~pre10-0ubuntu5                     OpenJDK Java runtime, using Hotspot JIT (headless)
ii  openjdk-6-jre-lib                      6b23~pre10-0ubuntu5                     OpenJDK Java runtime (architecture independent libraries)

```

---

### Post by spoolboyy on 2012-02-21
Anyone have any more info on this?  Is it some licensing thing with the whole Sun/Oracle situation?

I have manually installed the 'Beans on my 11.10 installation, but it was a pain and it shouldn't be as it never has been before.  I'd be interested in the explanation for why this just got harder.  I'm not upset, just curious as to why.

---

