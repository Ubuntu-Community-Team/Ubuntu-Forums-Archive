---
title: "Grub Error 15"
date: 2010-06-09
forum: General Help
---

### Post by Saxywolf on 2010-06-09
I know there are other posts about this, and even wiki pages on what to do, but I've followed them and still get the Error 15.

I updated ubuntu to 10.04 using the package manger, but when I rebooted I saw the regular boot menu, but when I selected Ubuntu, I got the following;
Boot from (hd1,0) ext3   [lots of numbers and letters]
Error 15: File not Found
Press any key to continue...

I could instead choose the Windows Vista from the boot menu and that still worked.

I tried multiple things. At one point I think I uninstalled all grub installations in what I think was an effort to remove all traces of the old grub before installing Grub 2. At another point I think I set it to install on all my partitions in '$ dpkg-reconfigure grub-pc' (it said to select all drives if you weren't sure which one to select using space to mark each one before hitting Enter and selecting just sdb1 hadn't worked).

I now get:
GRUB Loading stage1.5.
GRUB loading, please wait...
Error 15

It seems I tried to install the correct version:```
$ grub-install -v
grub-install (GNU GRUB 1.98-1ubuntu5)
```

My drives:```
$ sudo fdisk -l
Disk /dev/sda: 100.0 GB, yadda yadda
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       11300    90767218+   7  HPFS/NTFS
/dev/sda2           11301       12161     6915982+   7  HPFS/NTFS

Disk /dev/sdb: 100.0 GB, yadda yadda
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       11661    93666951   83  Linux
/dev/sdb2           11662       12161     4016250    5  Extended
/dev/sdb5           11662       12161     4016218+  82  Linux swap / Solaris

```however this doesn't work...```

$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).

```even after doing this:```

$ sudo mount /dev/sdb1 /mnt
```

I'm not even sure what this means, but it seemed to help somone else diagnose their install:```
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sda
eb48
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sda
0081
ubuntu@ubuntu:~$ sudo xxd -l 2 -p /dev/sdb
eb63
ubuntu@ubuntu:~$ sudo xxd -s 1049 -l 2 -p /dev/sdb
ffff
```

Downloaded the script: boot_info_script055.sh
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)```
ubuntu@ubuntu:~$ chmod 775 ~/Desktop/boot_info_script055.sh 
ubuntu@ubuntu:~$ sudo ~/Desktop/boot_info_script055.sh
...
 => Grub 0.97 is installed in the MBR of /dev/sda and looks on boot drive #2 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.
 => Grub 2 is installed in the MBR of /dev/sdb and looks on the same drive in 
    partition #1 for /boot/grub.
```

So, in the end it seems I have old and new grub installed, but I'm not sure how to remove the old one.

---

### Post by bcbc on 2010-06-09
The grub stage 1.5 is the grub-legacy boot loader as you see in the bootinfoscript. You could either boot from the second drive.

Or you can install the grub2 bootloader to /dev/sda by booting a live CD and running from terminal:
```
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

---

### Post by bcbc on 2010-06-09
> **Saxywolf said:**
> At another point I think I set it to install on all my partitions in '$ dpkg-reconfigure grub-pc' (it said to select all drives if you weren't sure which one to select using space to mark each one before hitting Enter and selecting just sdb1 hadn't worked).


If you did this then you've corrupted your windows bootsector and it won't boot anymore. See this link to restore the bootsector (using testdisk is the easiest method): [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

You can confirm this by checking your bootinfoscript results but since you didn't include the whole result I can't see.

---

### Post by john newbuntu on 2010-06-10
First change the BIOS boot order to boot from the second hard drive (sdb2)  and see if it is any better.
Edit: <I had the same suggestion as bcbc had in post #2>

---

### Post by Saxywolf on 2010-06-14
Thanks for your quick response. I read them over and followed the links. I finally prepared myself for doing more work that may lead to me doing something stupid and losing my data... so on with it.

I didn't see an error in RESULTS.txt like the one mentioned, so while the old Grub was on sda, I somehow didn't corrupt the boot sector.

I tried to change the boot order, but the BIOS only lists "laptop hard disk" (or some such) and does not list the 2 drives separately.


I'm not familiar with how grub and boot sectors work, but logically, I'd think that installing Grub to sda would corrupt the windows MBR.

However, I didn't think you'd tell me to do something that would in fact corrupt the MBR so I tried what you first suggested. And it worked. Thanks!

...

I am stumped at how I installed Grub to the windows drive, but didn't screw up it's boot sector.

---

### Post by bcbc on 2010-06-15
> **Saxywolf said:**
> Thanks for your quick response. I read them over and followed the links. I finally prepared myself for doing more work that may lead to me doing something stupid and losing my data... so on with it.

I didn't see an error in RESULTS.txt like the one mentioned, so while the old Grub was on sda, I somehow didn't corrupt the boot sector.

I tried to change the boot order, but the BIOS only lists "laptop hard disk" (or some such) and does not list the 2 drives separately.


I'm not familiar with how grub and boot sectors work, but logically, I'd think that installing Grub to sda would corrupt the windows MBR.

However, I didn't think you'd tell me to do something that would in fact corrupt the MBR so I tried what you first suggested. And it worked. Thanks!

...

I am stumped at how I installed Grub to the windows drive, but didn't screw up it's boot sector.

Great it all worked out :) 

It's good to question things you're told on the forums. It's safer and it's an opportunity to learn. 

I think this is a good site to learn about MBR's and PBR's, in particular, with regard to windows:  [http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

The windows boot loader (which goes in the MBR) is very limited - it will only boot the partition that's marked with the boot flag. And it's not required to boot windows (provided you have some alternative bootloader in place). That logic is all contained in the windows partition, so no harm in replacing the MBR with grub. In your case, you didn't even have the windows bootloader in the MBR, it was a grub-legacy bootloader left over from before you upgraded to 10.04.

---

