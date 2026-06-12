---
title: "I can't install the OpenJDK 7 PPA"
date: 2011-09-27
forum: General Help
---

### Post by eulyix on 2011-09-27
Hi,
I'm trying to use this repository: [https://launchpad.net/~openjdk/+archive/ppa]("https://launchpad.net/%7Eopenjdk/+archive/ppa")

$ lsb_release -cs
maverick

I take these steps to add it,

sudo add-apt-repository ppa:openjdk/ppa
sudo apt-get update

I then try sudo apt-get install openjdk-7. Doesn't work, despite that being the package name listed on the homepage. How confusing.

I look to see what OpenJDK 7 specific packages are now available.

openjdk-7-dbg - Java runtime based on OpenJDK (debugging symbols)
openjdk-7-demo - Java runtime based on OpenJDK (demos and examples)
openjdk-7-doc - OpenJDK Development Kit (JDK) documentation
openjdk-7-jdk - OpenJDK Development Kit (JDK)
openjdk-7-jre - OpenJDK Java runtime, using Hotspot JIT
openjdk-7-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
openjdk-7-jre-lib - OpenJDK Java runtime (architecture independent libraries)
openjdk-7-source - OpenJDK Development Kit (JDK) source files

Cool, I'll install openjdk-7-jdk. Faills, it depends on the jre, which depends on the headless package, which depends on the lib package which depends on the headless package... "There's a hole in my bucket, dear Liza..."

Can anyone help me here? Is this perhaps a problem with being on Ubuntu 10.10? I'd like to avoid upgrading again, if possible. It's funny how much easier it is to install the proprietary JDK 7 :p

Thanks.

---

### Post by Zvlwab on 2011-11-03
You should type:
apt-add-repository
instead of:
add-apt-repository

But now when I try to install openjdk-7, I get the following error:

```
me@laptop:~$ sudo apt-get install openjdk-7-jre openjdk-7-jdk openjdk-7-jre-headless openjdk-7-jre-lib 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openjdk-7-jdk : Conflicts: openjdk-7-jre (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
                 Conflicts: openjdk-7-jre-headless (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
 openjdk-7-jre : Conflicts: openjdk-7-jdk (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
                 Conflicts: openjdk-7-jre-headless (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
                 Conflicts: openjdk-7-jre-lib (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
 openjdk-7-jre-headless : Conflicts: openjdk-7-jdk (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
                          Conflicts: openjdk-7-jre (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
                          Conflicts: openjdk-7-jre-lib (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
 openjdk-7-jre-lib : Depends: openjdk-7-jre-headless (>= 7b89~pre1) but 7~b117~pre1-0maverick1 is to be installed
                     Conflicts: openjdk-7-jre (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
                     Conflicts: openjdk-7-jre-headless (< 7b89~pre1-0) but 7~b117~pre1-0maverick1 is to be installed
E: Broken packages
```I'm running Ubuntu 10.10 64-bit

---

