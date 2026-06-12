---
title: "Increase Partition Space When Installing Ubuntu On Windows"
date: 2010-03-18
forum: General Help
---

### Post by loweehahn on 2010-03-18
[SIZE=2]As we all know when installing ubuntu on Windows you'll be given only a maximum of 30GB partition for ubuntu. I would like to know if there's any way to increase the size. Thanks.[/SIZE]

---

### Post by TeoBigusGeekus on 2010-03-18
Why not dual boot?

---

### Post by loweehahn on 2010-03-18
Yeah I'm referring to dual boot actually.

---

### Post by TeoBigusGeekus on 2010-03-18
I don't get it... When you install ubuntu, you can give it whatever size you want, there are no limitations.

---

### Post by loweehahn on 2010-03-18
But when I install that time I had only a few choice of partition size. From 4GB to 30GB. I'm talking about installing ubuntu in Windows not installing ubuntu solely on it's own.

---

### Post by TeoBigusGeekus on 2010-03-18
Do you mean wubi?

---

### Post by loweehahn on 2010-03-18
Yes. I've forgotten the name.

---

### Post by TeoBigusGeekus on 2010-03-18
So then, I repeat my question: why not dual boot?

---

### Post by loweehahn on 2010-03-18
I'm dual booting. Why?

---

### Post by TeoBigusGeekus on 2010-03-18
I mean a clean, separate and independent installation of ubuntu - next to your windows installation.

---

### Post by loweehahn on 2010-03-18
I installed ubuntu inside Windows. As in opening windows, putting in the ubuntu CD and install through steps. Is that what you mean?

---

### Post by TeoBigusGeekus on 2010-03-18
No, I mean these:
[https://help.ubuntu.com/community/WindowsDualBoot]("https://help.ubuntu.com/community/WindowsDualBoot")
[http://oreilly.com/linux/archive/dual-boot-laptop.html]("http://oreilly.com/linux/archive/dual-boot-laptop.html")

---

### Post by rahulshah on 2010-03-18
i dont think you can increase the size of the partition to more than 30 GB. And yes until there is no special reason for u to use wubi, its better not to use it. Its not that reliable.... 

Enjoy :)

---

### Post by Baboontu on 2010-03-18
Dual boot is easy. use ubuntu live CD, install it and grub, the boot manager will take care of your windows OS automatically  by puting an entry inside the boot menu.
Good Luck!

---

### Post by loweehahn on 2010-03-18
After reading the page given by teobigusgeekus I understand the difference between wubi and dual boot. But why make two types of installation?

---

### Post by TeoBigusGeekus on 2010-03-18
Cause it's cleaner (sic), more stable and it runs faster. As simple as that...

---

### Post by loweehahn on 2010-03-18
You mean wubi or dual boot?

---

### Post by TeoBigusGeekus on 2010-03-18
Dual boot of course.

---

### Post by oldfred on 2010-03-18
Wubi allows beginners to try out Ubuntu. It is a little better than the liveCD since you can save settings, but it runs on NTFS in a windows partition and uses the windows boot loader. 
If you have decided you want to regularly use Ubuntu you should install to a separate partition as a regular install, true dual boot.

---

### Post by ram2500 on 2010-03-18
Wubi is a quick-and-easy solution, but for one, Windows will have a noticeable slowdown, for one, and Ubuntu won't perform as well as if it was a standalone installation, whether independent or by dual-boot. Ubuntu makes it easy to install alongside Windows, just make sure you back-up and have the installation media for Windows available. Normally, the Windows partition will be shown and will offer to install alongside Windows at the partitioning part of the installation. If it doesn't show and you do have Windows, STOP and DO NOT install--just get help. It is highly recommended to dual-boot for long-term installations.

---

### Post by loweehahn on 2010-03-19
I see. Thank you very much for telling me about this.

---

### Post by loweehahn on 2010-03-19
I've read about dual boot. It seems more dangerous than wubi.

---

### Post by oldfred on 2010-03-20
We consider running windows to be dangerous. At least with dual boot you have two ways to get into your system. IF the NTFS system gets corrupted, the wubi install also is corrupted. No system is perfectly safe, so we all have to rely on backups and multiple ways of doing things.

Wubi may be your best choice as it is for those who do not understand partitions but still want to try Ubuntu. But that limits you to the limits that running from a file give you. Your original question was for a larger allocation of space which is easy to do when you have separate partitions.

---

