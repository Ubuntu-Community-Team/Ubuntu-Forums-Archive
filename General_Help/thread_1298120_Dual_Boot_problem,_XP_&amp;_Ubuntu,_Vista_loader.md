---
title: "Dual Boot problem, XP &amp; Ubuntu, Vista loader"
date: 2009-10-22
forum: General Help
---

### Post by wang_chung on 2009-10-22
Hello
I'm having a problem dual booting Ubuntu (8.04) and XP, and I was hoping someone could give me some tips on how to fix it.
A long time ago, I just had XP installed. I then stupidly decided to try out a student trial version of Vista on a second harddrive, which I never used and which expired after a few months. Later, I installed Ubuntu, but couldn't get Grub to boot into XP. My present situation is Ubuntu is working lovely, and Grub has an option to start the Vista boot loader (this seemingly wasn't removed after I removed Vista). The Vista boot loader has two options - Vista, which just hangs (Vista isn't there anymore), and XP, which fails to load, complaining about a corrupt "ntldr". The XP installation is still there and I believe still intact (at one point I did a "fixmbr" using the XP CD and thereafter XP worked but I didn't have grub anymore).

When I run "fsdisk -l" I get this:
-----------------------------------------------------------------
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x03fb03fa

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          16       33479   268799580    7  HPFS/NTFS
/dev/sda2               1          15      120456   83  Linux
/dev/sda3           33480       38551    40740840   83  Linux
/dev/sda4           38552       38912     2899732+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x7bc6ddfd

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14946   120053713+  83  Linux
-----------------------------------------------------------------

The second harddrive is empty, Ubuntu is installed on a 40GB partition on the first harddrive, and XP is also on that drive. The "partition table entries not in disk order" info is a little disconcerting.


My grub menu.lst entries are as follows:
-----------------------------------------------------------------
title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic
root        (hd0,1)
kernel        /vmlinuz-2.6.24-24-generic root=UUID=abf71165-0b94-48c4-b398-28268679f0f7 ro quiet splash
initrd        /initrd.img-2.6.24-24-generic
quiet

title        Ubuntu 8.04.3 LTS, kernel 2.6.24-24-generic (recovery mode)
root        (hd0,1)
kernel        /vmlinuz-2.6.24-24-generic root=UUID=abf71165-0b94-48c4-b398-28268679f0f7 ro single
initrd        /initrd.img-2.6.24-24-generic


title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows Vista/Longhorn (loader)
root        (hd0,0)
chainloader    +1
-----------------------------------------------------------------


My question is: how do I fix the situation so that I can boot to Ubuntu or XP, preferably without reinstalling either OS?

Any help would be greatly appreciated.

---

### Post by utnubuuser on 2009-10-22
Tehre is an application available that will fix the mbr from ubuntu.  just google 'fix mbr ubuntu'

> [http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/]("http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/")

---

