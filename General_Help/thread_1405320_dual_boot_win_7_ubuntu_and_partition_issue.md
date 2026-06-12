---
title: "dual boot win 7 ubuntu and partition issue"
date: 2010-02-12
forum: General Help
---

### Post by lenoirrichelieu on 2010-02-12
Hi,
I have an issue related to a NTFS partition in Windos 7 after installing Ubuntu 9.10. First here it is my partition table:
 
HDD 1:
sda1 - NTFS - Win 7
sda2 - NTFS - Win XP
sda3 - ext4 - Ubuntu 9.10
sda4 - ext4 - for testing another distribution eventually
 
HDD 2:
sdb1 - NTFS - data
sdb2 - swap - for linux
 
After Ubuntu installation I use grub 2 as bootloader, which works without any issues. But now it happens from time to time I cannot see the partition sdb1 (which is NTFS as mentioned above) in Windows 7. It means it appears with the name (eg Data) but cannot be accesed and SO tells me it needs to be formatted.
 
I booted Ubuntu and from there that partition can be used normally, without any issue. So I tried 3 things:
1. chkdisk from command line in Win 7 - not working
2. booting Ubuntu, moving data and re-formatting that partition - not working
3. I installed ntfsprogs and I used in terminal *sudo ntfsfix /etc/dev/sdb1*. Then I rebooted Win 7. it appeared chkdisk which said the partiotion needs to be checked, I let the verification to be done, no issues found and then...surprise!. The partition is working normally in Win 7 .
 
My problem is that the steps mentioned at point 3 need to be done everytime the partition isn't seen. So I still didn't solve why it disappear. I even cannot tell when it disappear. I just find sometimes the partition ...is not there. Every time I boot in Ubuntu it is working normally. .
 
I thought is an issue related to grub 2. After some search I addes *GRUB_PRELOAD_MODULES=part_msdos* to */etc/default/grub* but no success.
 
this phenomenum apeared only after Ubuntu install 
 
Any idea please?

---

### Post by jken146 on 2010-02-12
Workaround: keep your shared files on an ext partition rather than NTFS.
[http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/](http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/)

---

### Post by lenoirrichelieu on 2010-02-12
Is not an issue about sharing files/folders between SOs. Is about missing a NTFS partition in Windows 7 after Ubuntu install.

---

### Post by jken146 on 2010-02-12
Yes, you're right. I can only tell you a workaround, not a solution. Perhaps the problem itself is more to do with Windows than Ubuntu.

---

### Post by lenoirrichelieu on 2010-02-15
I agree with this. I myself believe is something Win 7 related. But i made in mind the simple silogism:
I used A without problems
I installed B and now A has problems
So B modified/introduced something.
 
I don't say is necessarily a bug. I just don't get what happened. I don't get...I don't solve.
;)

---

