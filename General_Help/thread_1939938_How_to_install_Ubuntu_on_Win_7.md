---
title: "How to install Ubuntu on Win 7"
date: 2012-03-12
forum: General Help
---

### Post by amargarit on 2012-03-12
Hi to you all. I am new to this site and would like to know if anyone would be able to tell me how I can install Ubuntu 10.4 on a Win7 laptop so it could duel boot. I have around 19 gigs left and would really like to learn to use it.

Thanks

Anthony

---

### Post by Bucky Ball on 2012-03-12
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

There's a start. This will work fine for 10.04. Go to the section 'If Windows is already installed' but you probably won't need to shrink the Win7 partition (as you have 19Gb spare). Download the 10.04 LTS ISO and burn a disk, boot from that and 'Try Ubuntu'. See how it runs.  

For further research:

[http://au.search.yahoo.com/search;_ylt=A0oGkmCcfV5PDkgAG4YL5gt.?p=install%20ubunu%2010.04%20dual%20boot%20windows%207&fr2=sb-top&fr=altavista&rd=r1]("http://au.search.yahoo.com/search;_ylt=A0oGkmCcfV5PDkgAG4YL5gt.?p=install%20ubunu%2010.04%20dual%20boot%20windows%207&fr2=sb-top&fr=altavista&rd=r1")

---

### Post by amargarit on 2012-03-12
Thanks for such a quick reply Bucky Ball. I will try it and let you know how it went. Thanks so much.

:D

---

### Post by UnknownFearNG on 2012-03-12
Just a side-tip. If you don't have a CD lying around, you can also install it onto a USB stick.

---

### Post by Mark Phelps on 2012-03-13
If you're going to dual-boot, and you're currently running Win7 on your PC, then you need to do the following: Confirm that you don't already have the 4 Primary partition limit.  To do this, open the Win7 Disk Management utility and count the number of "drives" (that's what Windows calls partitions).  If you already have 4, then you're going to be faced with a LOT of work because you will have to remove one before you can create another for Ubuntu.

Also, check the "drive" types and confirm they are NOT Dynamic Disks.  Ubuntu can't be installed when Dynamic Disks are being used.

If you decide to go ahead with dual-boot, then do the following:
1) Use only the Win7 Disk Management utility to shrink your Win7 OS partition to make room for Ubuntu. Do NOT use the Ubuntu installer to do this. If you already have 4 partitions in Win7, do NOT allow the partitioner to create another partition.  This will convert your partitions into Dynamic Disks -- effectively preventing the installation of Ubuntu and causing you further problems.
2) Once you have Win7 shrunk, use the Win7 Backup feature to create and burn a Win7 Repair CD. This will come in handy later, should you need to repair your Win7 boot loader from the dual boot setup.

---

