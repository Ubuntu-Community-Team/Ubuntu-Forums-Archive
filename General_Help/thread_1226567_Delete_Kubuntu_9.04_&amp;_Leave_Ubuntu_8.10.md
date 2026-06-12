---
title: "Delete Kubuntu 9.04 &amp; Leave Ubuntu 8.10"
date: 2009-07-29
forum: General Help
---

### Post by pgibson on 2009-07-29
I've not found an answer searching, but I maybe missed it.

**Intrepid 'buntus replace WinXP (crowd cheers)**

My laptop's original hard drive was damaged in a fall and ceased to boot it's WinXP install.  I took it as an opportunity to make some changes.  I replaced the original 40GB drive with a 180GB one and replaced WinXP with Ubuntu 8.10 as my day-to-day operating system.  WinXP was plopped into a dark partition "just in case," (where it sits unused still) and I also installed Kubuntu 8.10 at the same time because I liked several of the KDE apps. 

**Unused Kubuntu upgrades to unused default (the cheek!)**

Kubuntu 8.10 never worked well on my machine, and upgrading it to Jaunty didn't improve things.   I never use it.  I would never even see it but that it became the default operating system in the upgrade and, unless I manually chose otherwise, it was what was booted at start up or a reboot.  I modified the menu.lst file in my Gnome install to point at my Ubuntu 8.10 install, but that didn't work because it never occurred to me that Kubuntu had a menu.lst too, (oops), and that was the one that grub would be looking at.  

**Kubuntu's boot gives greenhorn reason to give Kubuntu the boot!  (Huzzah!)**

Today, however, my Ubuntu 8.10 install system upgraded the Linux kernel to 2.6.28-14. for my Intrepid package, a change that never showed up on the Kubuntu menu.lst, though it is in the (unused?) menu.lst in the Ubuntu 8.10.

I've no doubt that it could all be straightened out --- even a greenhorn like me knows that almost anything is possible with Linux.  But I don't use Kubuntu and would rather just reclaim the space. than tinker with it.

GParted was what I used to partition the disk, would it be simplest to reclaim that partition?  And if I do this, will the menu.lst in my Ubuntu 8.10 install be the one that becomes used by grub?  Will it menu.lst update itself to use 28-14 "automagically?"  I am all a-flutter with anticipation.

Looking forward to a shinier machine.

Thanks in advance.

---

### Post by pgibson on 2009-07-30
Follow up:

Nevermind. After much reading, I found a semi-workaround.  

I backed up the Kubuntu menu.lst and replaced it with the Ubuntu menu.lst.  Kubuntu doesn't even show up, which is fine for now.

This is only a stop-gap measure.  I'll come back to it some other time.

Sorry the original post was so wordy.

---

