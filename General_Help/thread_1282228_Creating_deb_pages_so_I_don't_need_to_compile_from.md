---
title: "Creating deb pages so I don't need to compile from source again"
date: 2009-10-04
forum: General Help
---

### Post by madubuntuer on 2009-10-04
Hi,
I'm trying to build a LAMP server however because it's a dev server we have to compile php from source to ensure it's exactly the same as our host. I.e. same version of php with the same configuration and extensions.

I was wondering if it's possible to compile it/ build a deb package on my pc at home so I can just install the deb package at work. Compiling can take fairly long time and the dev server is P3 with limited ram. We're going to put more ram in but it may not be anytime soon. 

My greatest worry is the processor on my machine is intel core2 and the server has a p3. Would that cause any compatibility issues

---

### Post by Lars Noodén on 2009-10-04
Running the program **uname -m** one both machines should tell you if the OS is on the same architecture.  Since the package is to run on the PIII, you'll need the i386 (32-bit) version and not the amd64 (64-bit) version.  

You can cross-compile for i386, but maybe later.  Another option, one of several, is to install the dual-core computer dual boot, the second system being the i386 version of ubuntu.  You don't need a whole lot of space and you can even share the same home directory as the normal system.  

Once you have a 32-bit system to compile on, you'll want various related packages.  

Sorry there is a lot of material in the links below, as you go through and pick out the relevant parts, take notes and put up your own guide.  It is a piece of cake the second time, if you keep your notes. 

[http://www.debian.org/doc/maint-guide/](http://www.debian.org/doc/maint-guide/)
[http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/](http://tldp.org/HOWTO/html_single/Debian-Binary-Package-Building-HOWTO/)
[http://lyre.mit.edu/~powell/debian-howto/build-source.html](http://lyre.mit.edu/~powell/debian-howto/build-source.html)
[http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html](http://www.debian.org/doc/manuals/apt-howto/ch-sourcehandling.en.html)

---

### Post by geirha on 2009-10-04
There's also a guide at Ubuntu's wiki. [https://wiki.ubuntu.com/PackagingGuide](https://wiki.ubuntu.com/PackagingGuide)

---

### Post by Lars Noodén on 2009-10-04
Once you make your custom version of php, you'll want to keep it in place so it doesn't get over-written using APT pinning:
 [http://wiki.debian.org/AptPinning](http://wiki.debian.org/AptPinning)

---

### Post by credobyte on 2009-10-04
I suppose you are looking for something like checkinstall ( [https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall) ) ?

---

