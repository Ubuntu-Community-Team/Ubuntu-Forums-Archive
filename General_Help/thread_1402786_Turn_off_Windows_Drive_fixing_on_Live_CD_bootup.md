---
title: "Turn off Windows Drive fixing on Live CD bootup"
date: 2010-02-09
forum: General Help
---

### Post by bakegoodz on 2010-02-09
I have been using Ubuntu Live CD to get forensic (can't be modified in any way) images off of drives, but on dirty filesystems it does some type of fix on dirty Windows filesystems.

It has the message: File system wasn't safely closed on Windows fixing

How do I turn that off?

I create my own live CD, so I can modify what ever. Where is it? Initrd?

---

### Post by mörgæs on 2010-02-10
Does it have to be Ubuntu? There are many distros available, specially built for forensics.

---

### Post by bakegoodz on 2010-02-11
I am really partial to Debian based systems, I know were files are kept and how to add remove software from the command line. After further investigation I think that all the startup stuff is controlled by casper, but I have yet to find good documentation on customising casper.

---

### Post by bakegoodz on 2010-02-12
It might be the OS-Prober package that I installed with this guide: [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch)

I am going to remove it and see how the livecd works after

---

