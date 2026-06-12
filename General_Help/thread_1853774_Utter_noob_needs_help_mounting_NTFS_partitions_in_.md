---
title: "Utter noob needs help mounting NTFS partitions in Ubuntu"
date: 2011-10-02
forum: General Help
---

### Post by TitusPullo on 2011-10-02
Hi, I have a Windows 7 PC and just installed Ubuntu via VMWare Player.

I read that Ubuntu is supposed to detect NTFS volumes automatically and be able to read them out of the box.

Sadly my Ubuntu install does not detect any of my hard drives, which are all SATA drives. However it does detect my DVD drive, also connected via SATA.

So, I am totally new to Ubuntu and all this /etc/ and terminal stuff is baffling to me.

I tried adding physical drives using the VMWare settings, but when I do I get an error message saying some IDE setting is wrong.

What is the easiest way to do this? It's very simple, I need to transfer files easily between the Windows drives and the partition I gave to Ubuntu.

---

### Post by wolfen69 on 2011-10-03
> **TitusPullo said:**
> 
I read that Ubuntu is supposed to detect NTFS volumes automatically and be able to read them out of the box.



Yes it does, but only when you do a regular dual boot. By default, OS's in a virtual environment will not see any partitions outside of the virtual install itself.

I havn't used vmware in a while, but there should be a setting to share a folder between OS's in the settings.

---

### Post by 3rdalbum on 2011-10-03
The virtual machine cannot access hard disk partitions directly. If this was a real "on-the-hardware" installation of Ubuntu then the partitions would appear in the Unity bar on the left side of the screen, or in the Places menu (depending on what version of Ubuntu you are using).

To transfer files from the virtual Ubuntu to the Windows 7, you'll need to set up a shared folder. I'm not sure if VMWare Player supports this; probably not. Could you use a more full-featured virtualisation program such as Virtualbox, instead of VMware Player?

The reason the virtual machine can't access disks directly is to prevent the situation where a disk or partition is mounted or written-to simultaneously by more than one operating system, which would instantly corrupt the disk.

---

### Post by wildmanne39 on 2011-10-03
Hi, I am almost certain the way you want to do it is not possible in a virtual machine, if you had a normal install of ubuntu then it would be easy.

I use virtualbox and I use a shared folder, mine is documents and anything in that folder can be accessed by my virtual machine.
Thank you

---

### Post by TitusPullo on 2011-10-03
That makes sense.

VMWare does support folder sharing, I enabled it and chose a folder, but nothing has appeared in Ubuntu.

Maybe I should just redo the whole thing in VirtualBox?

---

### Post by wildmanne39 on 2011-10-03
Hi, my suggestion is to at the very least read the documentation for vmware, it should tell you how to use shared folders, but I am a big believer in virtualbox, and they have great documentation at there website, I always download virtualbox from the site also, if you go with it, you will need guest additions and extension pack.
[https://www.virtualbox.org/](https://www.virtualbox.org/)
Thank you

---

