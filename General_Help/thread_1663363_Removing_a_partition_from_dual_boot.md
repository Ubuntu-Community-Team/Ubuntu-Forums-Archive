---
title: "Removing a partition from dual boot"
date: 2011-01-09
forum: General Help
---

### Post by unbuntunewb on 2011-01-09
Hello,

I have windows xp on dual boot, however I do not use it anymore also something happened to the boot sector so now it wont work. I want to remove it so that I can have ubuntu reclaim the partition and have grub removed from startup. How does one do this?

---

### Post by wilee-nilee on 2011-01-09
> **unbuntunewb said:**
> Hello,

I have windows xp on dual boot, however I do not use it anymore also something happened to the boot sector so now it wont work. I want to remove it so that I can have ubuntu reclaim the partition and have grub removed from startup. How does one do this?

So it looks like you want to remove XP, and Just have Ubuntu, if this is so you need grub to boot Ubuntu. A single install of Ubuntu though generally doesn't show the grub menu unless you hold down a key. Please explain carefully what it is you want.

For a better picture of what is where do this, so from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the **(#)** in the reply panel this makes code tags paste all the text in between.

---

### Post by perspectoff on 2011-01-09
+1 

Rather than delete the XP partition, I'd just shrink it (using GParted) in order to reclaim space. However, it's a process that can cause problems if not done correctly. There is some info about manipulating partitions at Ubuntuguide.org:

[http://ubuntuguide.org/wiki/Manipulating_Partitions](http://ubuntuguide.org/wiki/Manipulating_Partitions)

and Kubuntuguide.org:

[http://kubuntuguide.org/Manipulating_Partitions](http://kubuntuguide.org/Manipulating_Partitions)

However, I agree with the previous post that you may be happier just repairing your Grub boot problems and leaving the XP partition be.

---

### Post by unbuntunewb on 2011-01-15
Sorry for any confusion.

So I use Ubuntu now as a primary OS, I also have xp on my computer on dual boot. One day I was in my windows files while I was using ubuntu and erased some stuff. I dont know what I erased but now windows xp will not boot. This is fine I do not use it anymore. So what I would like to do is completely remove XP from my hard drive and take back the 100 gigs I allocated to it and not have the grub menu at all. When I turn on my computer I want it to go straight to ubuntu. I have windows 7 on virtual box now anyway so I have no use for XP.

thank you!

---

### Post by ZebaSz on 2011-01-15
That being the case, I'd recommend you to boot from a LiveCD, run GParted, erase the Windows partition, and move/resize your other partitions.
It must be done from a LiveCD (at least the Ubuntu partition handling), since you can't resize them while mounted.
Deleting the partition is just enough, since GRUB then detects bootable partitions and updates the list.

---

### Post by ZebaSz on 2011-01-15
That being the case, I'd recommend you to boot from a LiveCD, run GParted, erase the Windows partition, and move/resize your other partitions.
It must be done from a LiveCD (at least the Ubuntu partition handling), since you can't resize them while mounted.
Deleting the partition is just enough, since GRUB then detects bootable partitions and updates the list.

---

### Post by ZebaSz on 2011-01-15
That being the case, I'd recommend you to boot from a LiveCD, run GParted, erase the Windows partition, and move/resize your other partitions.
It must be done from a LiveCD (at least the Ubuntu partition handling), since you can't resize them while mounted.
Deleting the partition is just enough, since GRUB then detects bootable partitions and updates the list.

---

### Post by ZebaSz on 2011-01-15
That being the case, I'd recommend you to boot from a LiveCD, run GParted, erase the Windows partition, and move/resize your other partitions.
It must be done from a LiveCD (at least the Ubuntu partition handling), since you can't resize them while mounted.
Deleting the partition is just enough, since GRUB then detects bootable partitions and updates the list.

---

### Post by ZebaSz on 2011-01-15
That being the case, I'd recommend you to boot from a LiveCD, run GParted, erase the Windows partition, and move/resize your other partitions.
It must be done from a LiveCD (at least the Ubuntu partition handling), since you can't resize them while mounted.
Deleting the partition is just enough, since GRUB then detects bootable partitions and updates the list.

---

