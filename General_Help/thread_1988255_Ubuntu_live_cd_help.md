---
title: "Ubuntu live cd help"
date: 2012-05-27
forum: General Help
---

### Post by z3rO88 on 2012-05-27
Hi, I have been looking around the Internet and on the forums for creating my own distribution of linux (live cd/dvd), are they any tutorials to follow that somebody can point out. :) thanks

---

### Post by lisati on 2012-05-27
*Thread moved to **General Help**.*

The "remastersys" package will let you create a live CD from your Ubuntu installation.

---

### Post by z3rO88 on 2012-05-27
i have tried remastersys, create a fullbackup which works, i basically need to strip ubuntu or a os and just add a few programs. would it be easier to strip a system or create my own distro ?

p.s. i tried ubuntu customized kit but when get to building it crashes and don't understand why

thanks for reply

---

### Post by zero2xiii on 2012-05-27
Hay,

I created a custom ubuntu distro for multimedia by doing a bare install inside a VM (vmware was used) then installing and setting up everything as I needed, then created an image using remastersys and it worked perfectly.

I would recommend this path as chroot'ing into stuff and all that can be a little daunting for some users. virtual box (I think) is free, so give that a try. In a virtual environment you have the luxury of a GUI and doing things the way you are used to. Just remember to make the "partition" or "drive" atleast twice the size of the FULL system. 20GB should give you more than enough room to spare for all the files.

Good luck :)
Cherz

---

### Post by z3rO88 on 2012-05-27
Thanks for the reply, i did the backup with remastersys, fullbackup it works fine, i was using laptop and vmware to do this but don't think it will be high enough for a final year project.

---

### Post by Strojar on 2012-05-28
i'm currently trying with ubuntu builder
[http://code.google.com/p/ubuntu-builder/](http://code.google.com/p/ubuntu-builder/)
you just need ubuntu mini remix iso image to build on.
[http://www.ubuntu-mini-remix.org/](http://www.ubuntu-mini-remix.org/)

---

