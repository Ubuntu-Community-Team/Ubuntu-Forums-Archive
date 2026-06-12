---
title: "upgraded windows dual boot/lucid-lost grub2"
date: 2011-05-08
forum: General Help
---

### Post by ejames82 on 2011-05-08
hi,

i had a dual boot with xp and lucid lynx, then upgraded the xp to win7.  windows commonly overwrites grub with it's bootloader.  and so it did.  now i can't access my lucid OS.  i need to get grub back (i need to get lucid back).  

here's my fdisk:

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x23213b72

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9561    76798701    7  HPFS/NTFS
/dev/sda2            9562       19336    78514176   83  Linux
Partition 2 does not end on cylinder boundary.
/dev/sda3           19336       19458      975872   82  Linux swap / Solaris
Partition 3 does not end on cylinder boundary.

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xb56fb56f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      182401  1465136001    7  HPFS/NTFS
ubuntu@ubuntu:~$ 



then i tried to get grub back myself, from instructions from a book:



ubuntu@ubuntu:~$ sudo grub-install /dev/sda
/usr/sbin/grub-probe: error: cannot find a device for /boot/grub (is /dev mounted?).
No path or device is specified.
Try `/usr/sbin/grub-probe --help' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.
ubuntu@ubuntu:~$ 



any help would be most appreciated.

---

### Post by Duncan Williams on 2011-05-08
try 
supergrub2
-worked for me last time I lost grub for natty/windowsXP dual boot.

---

### Post by ejames82 on 2011-05-08
Duncan Williams,

i don't know what you mean.
is that a command, as in:

sudo supergrub2

or some kind of program?

thanks for the reply

---

### Post by ajgreeny on 2011-05-08
Also look at [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) for all then ubuntu info on grub 2.

---

### Post by ejames82 on 2011-05-08
from tutorial provided by ajgreeney

13. reinstalling grub2 from live cd

since fdisk showed my ubuntu partition to be /dev/sda2


sudo mount /dev/sda2 /mnt

then:
nautilus /mnt
brought up my root file directory gui based (pictures of the folders in the root directory)

sudo grub-install /dev/sda

the terminal confirmed grub installed successfully without error.

thanks for the replies.

---

### Post by Duncan Williams on 2011-05-09
Sorry for not explaining better.
You can download **supergrub2** (1.4mb).
copy to blank cd.
boot up your pc with the cd with lost grub showing.
then go straight into os.

[http://www.bootproblems.com/](http://www.bootproblems.com/)

---

