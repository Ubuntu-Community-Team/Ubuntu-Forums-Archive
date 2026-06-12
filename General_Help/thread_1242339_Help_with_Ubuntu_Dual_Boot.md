---
title: "Help with Ubuntu Dual Boot"
date: 2009-08-17
forum: General Help
---

### Post by cvandor on 2009-08-17
Im going to try to make this as simple as possible while giving as much info as i can.  I just purchased an HP dv4t laptop with Vista Home Premium x64 preinstalled.  I installed firefox, avast AV, Spybot SD, Ad Aware and transferred my important docs from my old Win XP machine, including itunes music.  That's it. On the old machine i ran Ubuntu 9.04 through the Wubi installer and was very impressed.  I decided that I would like to dual boot with the new machine and went with an installation directly to the hard drive separate of windows.  what i would like to do is be able to share the main partition between both OS using NTFS format.  i want to be able to save the files and installations from vista in this process.  (link to my original post [http://ubuntuforums.org/showthread.php?t=1241878](http://ubuntuforums.org/showthread.php?t=1241878)) I have an above average knowledge of computer concepts but I will need some specific help with partitioning and terminal commands if neccessary.  Can someone help me please?

---

### Post by zvacet on 2009-08-17
If you want to install Ubuntu on separate drive then choose manual way to install and make root,home,shared and swap.Install root and shared as primary and home and swap as logical (extended partition).Separate home is good because that way you will save your settings if you decide to do fresh install in future. Format shared partition as NTFS because Ubuntu can read and write on it.

---

### Post by cvandor on 2009-08-17
okay how exactly would i do this if ive already installed ubuntu.  i may need more of a step-by-step instruction.

---

### Post by zvacet on 2009-08-17
Sorry for late response.If you already installed Ubuntu then first make separate home if you don´t have one.you can follow [this]("http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html") guide.Leave some unallocated space and format it as NTFS partition.You can also use [Gparted live CD.]("http://gparted.sourceforge.net/")

---

