---
title: "2 questions, 32or64 bit? / hard install OR along side(using wubi)"
date: 2011-05-08
forum: General Help
---

### Post by aliboy on 2011-05-08
1.which is better to use, the 32bit or 64bit version of 11.04?
2.is there a difference in terms of performance if you install ubuntu in a partition(hard install) and along side windows(using wubi)? Thank you!

---

### Post by Pand5461 on 2011-05-08
1. If you have a modern processor then 64-bit version is the choice. I don't think there's much difference in performance, though (unless you do sophisticated scientific calculations).
2. Disk performance is a bit lower in wubi version. Does not make it impossible to work. I'd recommend wubi if you are not familiar with hard disk partitioning (my friend once installed Ubuntu and accidentally formatted the whole partition with lots of docs).

---

### Post by Rubi1200 on 2011-05-08
Hi,
if your computer is 64-bit, then it probably makes sense to install the 64-bit version. However, I also know that people use 32-bit on 64-bit quite happily.

Wubi: there might be a slight performance hit using Wubi versus a partition install. Keep Windows defragmented and you should be okay.

If you decide to install via Wubi, make a copy of the root.disk and save it to an external medium as a quick backup method.

See more here:
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by aliboy on 2011-05-08
thanks for the reply!

---

### Post by lec0rsaire on 2011-05-08
If you have fairly new hardware with a 64-bit CPU I would install the 64-bit version. I'm running Maverick 64-bit on my new 1015pem netbook with the Atom N550 and 2 GB ram and it is surprisingly fast for what it is. I chose to install it with Wubi on my 2nd partition because I upgraded my Win 7 starter to Ultimate and have everything configured so in the event that GRUB would corrupt my mbr I would have lots of headaches starting over if something went wrong.

The Wubi install runs very well but obviously it is always ideal to have a "real" installation. I don't think you would see much gains in performance other than a faster Ubuntu boot though. I was up to my Win 7 partition limit with the EFI, Win 7, system recovery, and D: so I couldn't create another one on only 1 drive and I didn't want to dedicate half my hard drive for Ubuntu so Wubi was the perfect choice for me. However it may not be the right one for you. Give the Wubi install a try though. You have nothing to lose and it uninstalls cleanly in the event you change your mind.

---

### Post by sanderd17 on 2011-05-08
64-bit or 32-bit: don't worry, a normal user should not see a real difference.

As for wubi: first try ubuntu for a few months with wubi, then go to a dual boot (with a real install) and then wipe Windows. That's the path I followed about 2 years ago.

The biggest problem is that the stability of a wubi installation depends on windows. If windows makes something crash badly, your wubi installation might be gone. 

If you use wubi, you also have to use the ntfs filesystem. That is the filesystem used by windows and it's inferior to the ext4 or even ext3 that is commonly used in Linux. Ext* filesystems don't need defragmentation (they are designed in a way that creates no fragmentation) and they keep the user-rights (who can open,execute or write the file) together with the files.

So wubi is ideal for a long testing period (a couple of months) but not for a permanent used installation.

---

### Post by aliboy on 2011-05-08
thanks for sharing.

---

