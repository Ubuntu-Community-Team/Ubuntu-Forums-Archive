---
title: "Can't get it to run in virtualbox"
date: 2009-07-18
forum: General Help
---

### Post by Linux_noob616 on 2009-07-18
I'm using VirtualBox 3.0.2 and i've tried, Kubuntu, Ubuntu, and Xubuntu all 9.04 (even 9.10..) all x86-64

While they install fine, As soon as i install the guest additions the logon screen compresses to be just a thin line maybe an inch wide on my screen, can't read anything

If i can somehow log on then it works fine, Except everything runs chunky (even with hardware acceleration on..)

I also can't set up to use my share folder, gives me some protocol error about sbin/ .vbxsf (or whatever the virtual box share is called) doesn't exsist..

Help please.

---

### Post by hibliss on 2009-07-18
What is the host operating system?

---

### Post by Linux_noob616 on 2009-07-18
Windows 7 64bit

---

### Post by hibliss on 2009-07-18
I would try VMware instead for a Windows 7 host, or just check out Wubi if you want to test out Ubuntu.

---

### Post by Linux_noob616 on 2009-07-19
I dunno about now, But with 8.04 it felt bloated, and 8.10 hated my motherboard, Had no sound.

VMware hates Win7, well it hated the beta atleast

---

### Post by Linux_noob616 on 2009-07-20
Alright i installed VMware server. And now i dunno how to get it working, I can't even open a GUI.

Any ideas?

---

### Post by ZhuaSD on 2009-07-26
If you are installing Ubuntu on a Windows box, why not dual boot?  Just throw in the live disc, partition, and click the box to import the window's boot info into grub.

Obviously a different way but solves your problem quick.  Doubt you will find much support here, with a Win host...

---

