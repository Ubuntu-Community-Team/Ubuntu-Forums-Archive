---
title: "Need help turning iso image into hard disk image"
date: 2010-05-21
forum: General Help
---

### Post by Ghostnik11 on 2010-05-21
Hi, I wanted to run windows 7 virtually through virtualbox but the thing is I need an Hard Disk Image of windows 7, the problem is that I only have an iso image of windows 7.  So I wanted to know if there was a way to turn my iso image into a Hard Disk Image so I can then virutalize windows 7 through virtualbox.

---

### Post by ragtag on 2010-05-21
I'm guessing the Windows iso image is an image of the install dvd. To use it you'll need to create a virtual machine in VirtualBox and set up a virtual drive for it (big enough to take Win7). All this should be relatively straight forward in VirtualBox. You can then go into the CD settings for your machine and add the iso there. Once you start up the machine, it should boot up into the Windows 7 installer, and you install it like you would on a normal machine. 

That said, I've only used VirtualBox with Ubuntu Server, CentOS and WinXP as guest os's, so I'm not sure how well it works with Win7. :)

---

### Post by Ghostnik11 on 2010-05-21
Thanks worked perfectly as you said.  I am currently posting from my virtual windows 7 running through virtualbox.

---

