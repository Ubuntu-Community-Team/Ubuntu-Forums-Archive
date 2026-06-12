---
title: "Java and gcj"
date: 2009-09-07
forum: General Help
---

### Post by petersohn on 2009-09-07
Is it possible to install Ant (and other common Java applications) without gcj under Jaunty? I have the Sun JDK installed.

---

### Post by nikhilk on 2009-09-07
> **petersohn said:**
> Is it possible to install Ant (and other common Java applications) without gcj under Jaunty? I have the Sun JDK installed.

That seems possible. Check the package dependencies for ant [here]("/http://packages.ubuntu.com/jaunty/ant").

All gcj related dependencies also have sun-java alternatives, so you should be OK without installing gcj.

You can search for any other Java packages via the link above and check for the specific dependencies and alternatives.

---

### Post by petersohn on 2009-09-07
It says that I need openJDK then. What's that? I just don't want to have many Java implementations on my system.

---

### Post by nikhilk on 2009-09-07
> **petersohn said:**
> It says that I need openJDK then. What's that? I just don't want to have many Java implementations on my system.

You already have sun-java5-jre or sun-java6-jre package installed right? Then java2-runtime-headless should also be already installed. java2-runtime-headless is a virtual package provided by openjdk which is probably cause of this fuss.

Also, are you installing via Synaptic or command-line?

---

### Post by petersohn on 2009-09-07
I'm using Synaptic.

I have no package called java2-runtime-headless. Here is what I get if I search for it in command line:
```
$ apt-cache search headless
default-jre-headless - Standard Java or Java compatible Runtime (headless)
gij - The GNU Java bytecode interpreter
gij-4.3 - The GNU Java bytecode interpreter
java-gcj-compat-headless - Java runtime environment using GIJ (headless version)
gij-4.2 - The GNU Java bytecode interpreter
libtest-needsdisplay-perl - Ensure that tests needing a display have one
r-cran-rserve - GNU R Rserve tcp/ip server and sample clients
vlc-nox - multimedia player and streamer (without X support)
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
python-cupshelpers - Python modules for printer configuration with CUPS
sun-java5-jre - Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture independent files)
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
```

and my sources.list (without the comments):
```
deb http://archive.ubuntu.com/ubuntu/ jaunty main restricted                              
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates universe
deb http://archive.ubuntu.com/ubuntu/ jaunty multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-updates multiverse
deb http://archive.ubuntu.com/ubuntu/ jaunty-backports main restricted universe multiverse
deb http://archive.canonical.com/ubuntu jaunty partner
deb http://archive.ubuntu.com/ubuntu/ jaunty-security main restricted
deb http://archive.ubuntu.com/ubuntu/ jaunty-security universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ jaunty-security multiverse
deb http://ppa.launchpad.net/kubuntu-ppa/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/xorg-edgers/ppa/ubuntu jaunty main
deb http://ppa.launchpad.net/kubuntu-ppa/backports/ubuntu jaunty main

```

---

### Post by nikhilk on 2009-09-07
> **petersohn said:**
> I'm using Synaptic.

I have no package called java2-runtime-headless. Here is what I get if I search for it in command line:
```
$ apt-cache search headless
default-jre-headless - Standard Java or Java compatible Runtime (headless)
gij - The GNU Java bytecode interpreter
gij-4.3 - The GNU Java bytecode interpreter
java-gcj-compat-headless - Java runtime environment using GIJ (headless version)
gij-4.2 - The GNU Java bytecode interpreter
libtest-needsdisplay-perl - Ensure that tests needing a display have one
r-cran-rserve - GNU R Rserve tcp/ip server and sample clients
vlc-nox - multimedia player and streamer (without X support)
openjdk-6-jre-headless - OpenJDK Java runtime, using Hotspot JIT (headless)
python-cupshelpers - Python modules for printer configuration with CUPS
sun-java5-jre - Sun Java(TM) Runtime Environment (JRE) 5.0 (architecture independent files)
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
```

I am at work right now and can't check how to do it exactly but there has to be a way to select one package in case there are multiple choices for satisfying a dependency.

---

### Post by petersohn on 2009-09-08
I think I found the problem. It wanted to install every recommended package, so I had to turn it off.

---

