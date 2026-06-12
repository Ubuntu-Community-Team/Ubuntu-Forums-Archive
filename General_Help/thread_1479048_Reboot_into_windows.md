---
title: "Reboot into windows?"
date: 2010-05-10
forum: General Help
---

### Post by robincawser on 2010-05-10
Hi

I've been searching for the past hour for a script/program that will allow me, from Ubuntu, to reboot into windows (which I use for gaming). I assume this script would need to modify the grub.conf file in order to set a default OS for booting, and then to replace it with the original grub.conf.

I have found a [few]("http://robotics.caltech.edu/~klk/linux.html") scripts, but they are mostly obsolete since the move to grub2. Oh and also, I can't script for ****.

Any help would be much appreciated.

---

### Post by QIII on 2010-05-10
The only way I have ever heard to do this (which I have never used, so I can't even tell you how you might do it) is to use something like kexec-tools.

Basically, it loads a new kernel in memory (this does not have to be a Linux kernel), bypassing the BIOS restart.

Again:  I have never done this and I don't know what dangers may be involved.

If you have some time, I would google "site:ubuntuforums.org kexec-tools".  I found several threads, but don't have the time right now to go through them to see if there were any resolutions to the problems people were having.

---

### Post by robincawser on 2010-05-10
> **QIII said:**
> 
Basically, it loads a new kernel in memory (this does not have to be a Linux kernel), bypassing the BIOS restart.


That does sound pretty scary.

[I just read this on shuttleworth's blog]("http://www.markshuttleworth.com/archives/383")

> The Ubuntu Light range is available to OEM&#8217;s today. Each image will be hand-crafted to boot fastest on that specific hardware, the application load reduced to the minimum, **and it comes with tools for Windows which assist in the management of the dual-boot experience**. Initially, the focus is on the Netbook Light version based on Unity, but in future we expect to do a Light version of the desktop, too.

[IMG]http://i.imgur.com/G085d.png[/IMG]

Do you think the tools he is referring to already exist or are being developed? Because that looks like exactly what I need.

---

### Post by robincawser on 2010-05-12
Any one had any ideas?

---

