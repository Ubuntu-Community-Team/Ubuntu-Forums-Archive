---
title: "How would I install a second OS with virtualbox?"
date: 2010-07-25
forum: General Help
---

### Post by Dustin2128 on 2010-07-25
I remember reading a post under [the coolest thing I've ever done on ubuntu]("http://ubuntuforums.org/showthread.php?t=1537627") about installing windows to a raw partition using VirtualBox in order to create a dual-boot. I was wondering how to do that, because I'd like a live environment so I can look at the install guide while I install gentoo (livecd was unavailible for my architecture). Any tutorials?

---

### Post by cj.surrusco on 2010-07-25
I'm pretty sure you have to make a .vmdk of an empty partition to do that. It explains how to do that in part of [this]("http://ubuntuforums.org/showthread.php?t=769883") howto. That howto is actually also pretty cool, allowing to boot into windows either normally, or in a virtual machine. 

Just follow step two to do what you are asking for. Then you can create a new virtual machine and mount that new .vmdk, and install Windows.

---

