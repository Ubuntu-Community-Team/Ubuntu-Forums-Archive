---
title: "unetbootin, failure to boot after creation"
date: 2012-07-14
forum: General Help
---

### Post by F W Adams on 2012-07-14
I went through the USB creation process but am now unable to boot from the usb. I know my bios is caplable of booting USB's.

host: ubuntu 12.04
create usb: ubuntu 10.04 live, capacity is 4GB
selected 200MB persistent 

Directory of usb

felix@xxx:~$ ls -l /media/KINGSTON
total 207152
-rw-r--r-- 1 felix felix       166 Apr 14  2010 autorun.inf
-rw-r--r-- 1 felix felix 209715200 Jul 14 12:15 casper-rw
-r--r--r-- 1 felix felix     32768 Jul 14 12:13 ldlinux.sys
-rw-r--r-- 1 felix felix     60928 Jul 14 12:13 menu.c32
-rw-r--r-- 1 felix felix       156 Jul 14 12:13 syslinux.cfg
-rw-r--r-- 1 felix felix         0 Jul 14 12:13 ubnfilel.txt
-rw-r--r-- 1 felix felix         0 Jul 14 12:13 ubnpathl.txt
-rwxr-xr-x 1 felix felix    361248 Sep 14  2011 unInstaller.exe
drwx------ 4 felix felix      4096 May  5 10:20 urDrive
-rwxr-xr-x 1 felix felix   1934624 Sep 14  2011 urDrive.exe


On attempting to boot there is a countdown timer that starts at 10, when it reaches 0 it just starts at 10 again

The tab key produces,
">ubnkern initrd=/ubninit persistent"

Thanks for any help

---

### Post by Cheesehead on 2012-07-14
Double-check that you used a valid 10.04 image.
Try making the USB Stick again.

The directory listing you posted seems to have neither a kernel or a compressed-system to use that kernel, both of which come from the 10.04 image.

---

### Post by F W Adams on 2012-07-15
Thanks for infomation

This is where I got it from. A fresh the iso image was downloaded by the program in each case.
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

To my amazement this time the result was different, there are even less files put onto the usb. This looks to me to be some sort of buffer problem, at least that's my guess. The corrent files being sent to the usb by the program ( unetbootin-linux-575 ) but then not being written to the usb before closing down. Any ideas?

First try, selected reboot at end
Second try, selected exit and then closed down
Will now try exit, list usb files, umount usb, and then closing down?

felix@emma:~$ ls -l -R /media/KINGSTON
/media/KINGSTON:
total 204896
-rw-r--r-- 1 felix felix 209715200 Jul 15 00:30 casper-rw
-r--r--r-- 1 felix felix     32768 Jul 15 00:29 ldlinux.sys
-rw-r--r-- 1 felix felix     60928 Jul 15 00:29 menu.c32
-rw-r--r-- 1 felix felix       156 Jul 15 00:29 syslinux.cfg
-rw-r--r-- 1 felix felix         0 Jul 15 00:29 ubnfilel.txt
-rw-r--r-- 1 felix felix         0 Jul 15 00:29 ubnpathl.txt

---

### Post by F W Adams on 2012-07-15
You can see here it is just not putting on all the files on the USB. Next I'll try downloading an ISO image from this site and then comparing it to the one I'm already using.

felix@emma:~/unetbootin$ sudo ./unetbootin-linux-575
felix@emma:~/unetbootin$ ls -l /media/form-15.07-
total 204896
-rw-r--r-- 1 felix felix 209715200 Jul 15 09:40 casper-rw
-r--r--r-- 1 felix felix     32768 Jul 15 09:38 ldlinux.sys
-rw-r--r-- 1 felix felix     60928 Jul 15 09:38 menu.c32
-rw-r--r-- 1 felix felix       156 Jul 15 09:38 syslinux.cfg
-rw-r--r-- 1 felix felix         0 Jul 15 09:38 ubnfilel.txt
-rw-r--r-- 1 felix felix         0 Jul 15 09:38 ubnpathl.txt
felix@emma:~/unetbootin$ ls -l /media/form-15.07- > before.reboot.575

---

### Post by sudodus on 2012-07-15
Maybe the following links will help you pass the threshold :-)

Unetbootin (see the last post):
[[COLOR="Red"]_http://ubuntuforums.org/showthread.php?t=1885392_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1885392")

Cloning the iso file:
[[COLOR="red"]_http://ubuntuforums.org/showthread.php?t=1958073_[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1958073")

---

### Post by F W Adams on 2012-07-15
I have isolsted the problem a bit but not solved.

It makes no difference what OS or iso I try to load, the list of files copied to the drive varies each time and of course it never boots.

I'd be very surprised if it's a unetbootin problem now. I tried a different usb drive by a different manufacturer and unetbootin for that worked fine. I bought 4 new USB drives last week, all the same manufacturer ( KINGSTON ) and none of them work. It comes with something called urDrive that seems difficult to get rid of.

I tried "dd if=xxx.img of=/dev/sd?" and seems to copy the image but won't boot.

I even tried "dd if=/dev/zero of=/dev/sd? bs=4096" to try and destroy whatever is on the USB but after creating the partition table again etc etc. it was still the same. I am wondering if the usb appears to be something that it is not.

Wasted hours on this.

---

### Post by sudodus on 2012-07-15
> **F W Adams said:**
> I have isolsted the problem a bit but not solved.

It makes no difference what OS or iso I try to load, the list of files copied to the drive varies each time and of course it never boots.

I'd be very surprised if it's a unetbootin problem now. I tried a different usb drive by a different manufacturer and unetbootin for that worked fine. I bought 4 new USB drives last week, all the same manufacturer ( KINGSTON ) and none of them work. It comes with something called urDrive that seems difficult to get rid of.

I tried "dd if=xxx.img of=/dev/sd?" and seems to copy the image but won't boot.

I even tried "dd if=/dev/zero of=/dev/sd? bs=4096" to try and destroy whatever is on the USB but after creating the partition table again etc etc. it was still the same. I am wondering if the usb appears to be something that it is not.

Wasted hours on this.

I think you know what to do, and that the problem is actually because of the USB drives. But maybe it is worth trying a little more before giving up. I guess you have a partition with FAT32 now. Please run the following commands and post the output in a reply!
```
sudo fdisk -lu
```
```
df
```
Maybe you can try the following command after Unetbootin to force the system to finish writing to the flash memory.
```
sync
```
When the prompt returns after *sync*, all the files should be written, otherwise the USB drives are not cooperating properly with Ubuntu.

Maybe those Kingston drives are slow, so that you must wait a while to let it finish writing. If there is a LED, you can see it flashing while reading or writing, otherwise it is difficult to know, but it might help to use *sync*.

---

### Post by F W Adams on 2012-07-15
Agree over usb's, would rather get them working though. I think I may have got two different usb's confused when I concluded "dd if=/dev/zero of=/dev/sd? bs=4096" didn't help. The symptoms are at least changed,

Here is what you asked for:

```
felix@emma:~$ sudo fdisk -lu
[sudo] password for felix: 

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099408

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   112304127    56151040   83  Linux
/dev/sda2       112306174   124510207     6102017    5  Extended
/dev/sda3   *   124510208   125044735      267264   83  Linux
/dev/sda5       112306176   124510207     6102016   83  Linux

Disk /dev/sdb: 300.1 GB, 300089646592 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586112591 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08040000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/sdc: 3869 MB, 3869544448 bytes
105 heads, 18 sectors/track, 3998 cylinders, total 7557704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00014e59

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048     7557119     3777536    b  W95 FAT32

Disk /dev/mapper/sda1_crypt: 57.5 GB, 57496567808 bytes
255 heads, 63 sectors/track, 6990 cylinders, total 112297984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda1_crypt doesn't contain a valid partition table

Disk /dev/mapper/lvm0-swap: 1497 MB, 1497366528 bytes
255 heads, 63 sectors/track, 182 cylinders, total 2924544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lvm0-swap doesn't contain a valid partition table

Disk /dev/mapper/lvm0-system: 5997 MB, 5997854720 bytes
255 heads, 63 sectors/track, 729 cylinders, total 11714560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lvm0-system doesn't contain a valid partition table

Disk /dev/mapper/lvm0-home: 50.0 GB, 50000297984 bytes
255 heads, 63 sectors/track, 6078 cylinders, total 97656832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lvm0-home doesn't contain a valid partition table
felix@emma:~$ 
felix@emma:~$ 
felix@emma:~$ df
Filesystem              1K-blocks    Used Available Use% Mounted on
/dev/mapper/lvm0-system   5840404 2549204   2998336  46% /
udev                      2035044       4   2035040   1% /dev
tmpfs                      818192     876    817316   1% /run
none                         5120       0      5120   0% /run/lock
none                      2045472     152   2045320   1% /run/shm
/dev/sda3                  264491   46023    205105  19% /boot
/dev/mapper/lvm0-home    48728816 2660312  43627084   6% /home
/dev/sda5                 6084608  221536   5557972   4% /home/fast.ne
/dev/sdc1                 3770152   34044   3736108   1% /media/u10.04
felix@emma:~$

```

After trying again 

"dd if=/dev/zero of=/dev/sd? bs=4096"
and then creating a new partition table and partition with gparted
and then trying unetbootin followed by "sync" I got:

```
felix@emma:~/unetbootin$ cat after.dd.dos
total 33764
-rw-r--r-- 1 felix felix      143 Feb 14 11:49 autorun.inf
drwx------ 2 felix felix     4096 Jul 15 22:53 casper
-rw-r--r-- 1 felix felix 20971520 Jul 15 22:15 casper-rw
drwx------ 3 felix felix     4096 Jul 15 22:41 dists
drwx------ 2 felix felix     4096 Jul 15 22:41 install
drwx------ 2 felix felix     4096 Jul 15 22:41 isolinux
-r--r--r-- 1 felix felix    32768 Jul 15 22:15 ldlinux.sys
-rw-r--r-- 1 felix felix    60928 Jul 15 22:15 menu.c32
drwx------ 2 felix felix     4096 Jul 15 22:41 pics
drwx------ 4 felix felix     4096 Jul 15 22:41 pool
drwx------ 2 felix felix     4096 Jul 15 22:41 preseed
-rw-r--r-- 1 felix felix      227 Feb 14 11:51 README.diskdefines
-rw-r--r-- 1 felix felix  9419899 Feb 14 10:50 ubninit
-rw-r--r-- 1 felix felix  4048512 Jan  4  2012 ubnkern
-rw-r--r-- 1 felix felix        0 Jul 15 22:53 ubnpathl.txt

```
a lot better than this morning, well, my morning anyway, see below

```
felix@emma:~/unetbootin$ cat before.reboot.578
total 204896
-rw-r--r-- 1 felix felix 209715200 Jul 15 09:59 casper-rw
-r--r--r-- 1 felix felix     32768 Jul 15 09:56 ldlinux.sys
-rw-r--r-- 1 felix felix     60928 Jul 15 09:57 menu.c32
-rw-r--r-- 1 felix felix       156 Jul 15 09:56 syslinux.cfg
-rw-r--r-- 1 felix felix         0 Jul 15 09:56 ubnfilel.txt
-rw-r--r-- 1 felix felix         0 Jul 15 09:56 ubnpathl.txt

```

It even made a good try at booting, I got the message:

"SYSLINUX 4.03 2010-10-22 .......
ERROR: No configuration file found
No default UI or configuration directive found
Boot:"

Thanks for helping me out.

---

### Post by sudodus on 2012-07-16
Yes, you are making progress. The output of fdisk and df look good, and you copied more files. Can you check with the working USB pendrive (of another make) if all files were copied?

May I suggest that next time you try to clone the working USB pendrive (of another make) to another of the Kingston USB pendrives (not overwriting what is almost working). Since you know dd, you can use that, just make sure to identify the drive letters correctly. Run sync afterwards and wait some extra time for the writing to finish.

I guess if you insert the working USB pendrive (of another make) first, it will be seen as **[FONT="Courier New"][SIZE="3"]/dev/sdc[/SIZE][/FONT]** and the other Kingston USB pendrive will be seen as **[FONT="Courier New"][SIZE="3"]/dev/sdd[/SIZE][/FONT]** but check to be sure before substituting X and Y in the following command line

```
dd if=/dev/sdX of=/dev/sdY bs=4096
```

---

### Post by F W Adams on 2012-07-16
I went and bought another flash USB today and set it up, it was fine.

I did as you suggested but rather as expected it didn't work. The transfer was of about 1GB from partition 1 of the ok system ( sdd1 ) to the bad one ( sdc1 ). SYNC took about 15 seconds so definately necessary. As expected it turned it into a 1GB device. I haven't looked in detail but the files seem fine, the disk label was transferred as well, it doesn't show as I changed the label of the ok one afterwards. Bad one: according to fdisk the format is FAT16, as it was before the transfer, but gparted has it as FAT16 before the transfer and F32 afterwrds. When booting there was just a blank screen.


fdisk, mount & two ls -l -R

```
felix@emma:~$ 
felix@emma:~$ sudo fdisk -l

Disk /dev/sda: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders, total 125045424 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00099408

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   112304127    56151040   83  Linux
/dev/sda2       112306174   124510207     6102017    5  Extended
/dev/sda3   *   124510208   125044735      267264   83  Linux
/dev/sda5       112306176   124510207     6102016   83  Linux

Disk /dev/sdb: 300.1 GB, 300089646592 bytes
255 heads, 63 sectors/track, 36483 cylinders, total 586112591 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x08040000

Disk /dev/sdb doesn't contain a valid partition table

Disk /dev/mapper/sda1_crypt: 57.5 GB, 57496567808 bytes
255 heads, 63 sectors/track, 6990 cylinders, total 112297984 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda1_crypt doesn't contain a valid partition table

Disk /dev/mapper/lvm0-swap: 1497 MB, 1497366528 bytes
255 heads, 63 sectors/track, 182 cylinders, total 2924544 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lvm0-swap doesn't contain a valid partition table

Disk /dev/mapper/lvm0-system: 5997 MB, 5997854720 bytes
255 heads, 63 sectors/track, 729 cylinders, total 11714560 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lvm0-system doesn't contain a valid partition table

Disk /dev/mapper/lvm0-home: 50.0 GB, 50000297984 bytes
255 heads, 63 sectors/track, 6078 cylinders, total 97656832 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/lvm0-home doesn't contain a valid partition table

Disk /dev/sdc: 3869 MB, 3869544448 bytes
105 heads, 18 sectors/track, 3998 cylinders, total 7557704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009020b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048     7557119     3777536    6  FAT16

Disk /dev/sdd: 3999 MB, 3999268864 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63     2152709     1076323+   b  W95 FAT32
/dev/sdd2         2152710     7807589     2827440    b  W95 FAT32
felix@emma:~$ 
felix@emma:~$ 
felix@emma:~$ 
felix@emma:~$ sudo mount
/dev/mapper/lvm0-system on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda3 on /boot type ext4 (rw)
/dev/mapper/lvm0-home on /home type ext4 (rw)
/dev/sda5 on /home/fast.ne type ext4 (rw)
gvfs-fuse-daemon on /home/felix/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=felix)
/dev/sdc1 on /media/u10.04 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdd1 on /media/U12~04~1k type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
/dev/sdd2 on /media/p2 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)
felix@emma:~$ 
felix@emma:~$ 
felix@emma:~$ 
felix@emma:~$ ls -l -R /media/U12~04~1k
/media/U12~04~1k:
total 226836
-rw-r--r-- 1 felix felix       134 Apr 23 13:27 autorun.inf
drwx------ 3 felix felix      4096 Jul 16 11:13 boot
drwx------ 2 felix felix      4096 Jul 16 11:46 casper
-rw-r--r-- 1 felix felix 209715200 Jul 16 12:53 casper-rw
drwx------ 4 felix felix      4096 Jul 16 11:13 dists
drwx------ 2 felix felix      4096 Jul 16 11:17 install
drwx------ 2 felix felix     12288 Jul 16 11:17 isolinux
-r--r--r-- 1 felix felix     32768 Jul 16 11:17 ldlinux.sys
-rw-r--r-- 1 felix felix      4237 Apr 23 13:27 md5sum.txt
-rw-r--r-- 1 felix felix     60928 Jul 16 11:17 menu.c32
drwx------ 2 felix felix      4096 Jul 16 11:17 pics
drwx------ 4 felix felix      4096 Jul 16 10:31 pool
drwx------ 2 felix felix      4096 Jul 16 11:17 preseed
-rw-r--r-- 1 felix felix       231 Apr 23 13:27 README.diskdefines
-rw-r--r-- 1 felix felix      1041 Jul 16 11:17 syslinux.cfg
-rw-r--r-- 1 felix felix      4478 Jul 16 11:17 ubnfilel.txt
-rw-r--r-- 1 felix felix  14873857 Apr 23 13:27 ubninit
-rw-r--r-- 1 felix felix   5015840 Apr 23 13:27 ubnkern
-rw-r--r-- 1 felix felix       318 Jul 16 11:13 ubnpathl.txt
-rw-r--r-- 1 felix felix         0 Feb 14 11:51 ubuntu
-rwxr-xr-x 1 felix felix   2502608 Apr 23 13:27 wubi.exe

/media/U12~04~1k/boot:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:13 grub

/media/U12~04~1k/boot/grub:
total 4
-rw-r--r-- 1 felix felix 589 Apr 23 13:27 loopback.cfg

/media/U12~04~1k/casper:
total 708076
-rw-r--r-- 1 felix felix     41315 Apr 23 13:27 filesystem.manifest
-rw-r--r-- 1 felix felix     38275 Feb 14 10:48 filesystem.manifest-desktop
-rw-r--r-- 1 felix felix      1079 Apr 23 13:27 filesystem.manifest-remove
-rw-r--r-- 1 felix felix        11 Apr 23 13:27 filesystem.size
-rw-r--r-- 1 felix felix 704692224 Apr 23 13:27 filesystem.squashfs
-rw-r--r-- 1 felix felix  15263318 Jul 16 11:46 initrd.lz
-rw-r--r-- 1 felix felix   5015840 Apr 23 13:27 vmlinuz

/media/U12~04~1k/dists:
total 8
drwx------ 4 felix felix 4096 Jul 16 10:34 lucid
drwx------ 4 felix felix 4096 Jul 16 11:17 precise
-rw-r--r-- 1 felix felix    0 Feb 14 11:51 stable
-rw-r--r-- 1 felix felix    0 Feb 14 11:51 unstable

/media/U12~04~1k/dists/lucid:
total 16
drwx------ 4 felix felix 4096 Jul 16 10:31 main
-rw-r--r-- 1 felix felix 1759 Feb 14 11:51 Release
-rw-r--r-- 1 felix felix  198 Feb 14 11:51 Release.gpg
drwx------ 4 felix felix 4096 Jul 16 10:31 restricted

/media/U12~04~1k/dists/lucid/main:
total 8
drwx------ 2 felix felix 4096 Jul 16 10:34 binary-i386
drwx------ 2 felix felix 4096 Jul 16 10:31 source

/media/U12~04~1k/dists/lucid/main/binary-i386:
total 16
-rw-r--r-- 1 felix felix 9400 Feb 14 11:51 Packages.gz
-rw-r--r-- 1 felix felix   94 Feb 14 11:51 Release

/media/U12~04~1k/dists/lucid/main/source:
total 0

/media/U12~04~1k/dists/lucid/restricted:
total 8
drwx------ 2 felix felix 4096 Jul 16 10:34 binary-i386
drwx------ 2 felix felix 4096 Jul 16 10:31 source

/media/U12~04~1k/dists/lucid/restricted/binary-i386:
total 8
-rw-r--r-- 1 felix felix 1270 Feb 14 11:51 Packages.gz
-rw-r--r-- 1 felix felix  100 Feb 14 11:51 Release

/media/U12~04~1k/dists/lucid/restricted/source:
total 0

/media/U12~04~1k/dists/precise:
total 16
drwx------ 4 felix felix 4096 Jul 16 11:13 main
-rw-r--r-- 1 felix felix 1765 Apr 23 13:27 Release
-rw-r--r-- 1 felix felix  198 Apr 23 13:27 Release.gpg
drwx------ 4 felix felix 4096 Jul 16 11:13 restricted

/media/U12~04~1k/dists/precise/main:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 binary-i386
drwx------ 2 felix felix 4096 Jul 16 11:13 source

/media/U12~04~1k/dists/precise/main/binary-i386:
total 12
-rw-r--r-- 1 felix felix 7427 Apr 23 13:27 Packages.gz
-rw-r--r-- 1 felix felix   96 Apr 23 13:27 Release

/media/U12~04~1k/dists/precise/main/source:
total 0

/media/U12~04~1k/dists/precise/restricted:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 binary-i386
drwx------ 2 felix felix 4096 Jul 16 11:13 source

/media/U12~04~1k/dists/precise/restricted/binary-i386:
total 8
-rw-r--r-- 1 felix felix 1406 Apr 23 13:27 Packages.gz
-rw-r--r-- 1 felix felix  102 Apr 23 13:27 Release

/media/U12~04~1k/dists/precise/restricted/source:
total 0

/media/U12~04~1k/install:
total 1620
-rw-r--r-- 1 felix felix  176764 Apr 23 13:27 mt86plus
-rw-r--r-- 1 felix felix    1865 Apr 23 13:27 README.sbm
-rw-r--r-- 1 felix felix 1474560 Apr 23 13:27 sbm.bin

/media/U12~04~1k/isolinux:
total 1328
-rw-r--r-- 1 felix felix  71280 Apr 23 13:27 16x16.fnt
-rw-r--r-- 1 felix felix   3404 Apr 23 13:27 access.pcx
-rw-r--r-- 1 felix felix      0 Feb 14 11:51 adtext.cfg
-rw-r--r-- 1 felix felix      0 Apr 23 13:27 adtxt.cfg
-rw-r--r-- 1 felix felix   2967 Apr 23 13:27 am.tr
-rw-r--r-- 1 felix felix   7340 Apr 23 13:27 ast.hlp
-rw-r--r-- 1 felix felix   2007 Apr 23 13:27 ast.tr
-rw-r--r-- 1 felix felix   7500 Apr 23 13:27 back.jpg
-rw-r--r-- 1 felix felix  11711 Apr 23 13:27 be.hlp
-rw-r--r-- 1 felix felix   3483 Apr 23 13:27 be.tr
-rw-r--r-- 1 felix felix  11704 Apr 23 13:27 bg.hlp
-rw-r--r-- 1 felix felix   3869 Apr 23 13:27 bg.tr
-rw-r--r-- 1 felix felix  11457 Apr 23 13:27 blank.pcx
-rw-r--r-- 1 felix felix  15128 Apr 23 13:27 bn.hlp
-rw-r--r-- 1 felix felix   2048 Apr 23 13:27 boot.cat
-rw-r--r-- 1 felix felix 108032 Apr 23 13:27 bootlogo
-rw-r--r-- 1 felix felix   7082 Apr 23 13:27 bs.hlp
-rw-r--r-- 1 felix felix   1950 Apr 23 13:27 bs.tr
-rw-r--r-- 1 felix felix   8050 Apr 23 13:27 ca.hlp
-rw-r--r-- 1 felix felix   2243 Apr 23 13:27 ca.tr
-rw-r--r-- 1 felix felix  20704 Apr 23 13:27 chain.c32
-rw-r--r-- 1 felix felix   7383 Apr 23 13:27 cs.hlp
-rw-r--r-- 1 felix felix   2135 Apr 23 13:27 cs.tr
-rw-r--r-- 1 felix felix   6907 Apr 23 13:27 da.hlp
-rw-r--r-- 1 felix felix   1971 Apr 23 13:27 da.tr
-rw-r--r-- 1 felix felix   7749 Apr 23 13:27 de.hlp
-rw-r--r-- 1 felix felix   2196 Apr 23 13:27 de.tr
-rw-r--r-- 1 felix felix   1423 Apr 23 13:27 dtmenu.cfg
-rw-r--r-- 1 felix felix  13417 Apr 23 13:27 el.hlp
-rw-r--r-- 1 felix felix   4061 Apr 23 13:27 el.tr
-rw-r--r-- 1 felix felix   6501 Apr 23 13:27 en.hlp
-rw-r--r-- 1 felix felix   1759 Apr 23 13:27 en.tr
-rw-r--r-- 1 felix felix   6874 Apr 23 13:27 eo.hlp
-rw-r--r-- 1 felix felix   1928 Apr 23 13:27 eo.tr
-rw-r--r-- 1 felix felix   7586 Apr 23 13:27 es.hlp
-rw-r--r-- 1 felix felix   2037 Apr 23 13:27 es.tr
-rw-r--r-- 1 felix felix   6742 Apr 23 13:27 et.hlp
-rw-r--r-- 1 felix felix   1895 Apr 23 13:27 et.tr
-rw-r--r-- 1 felix felix   7173 Apr 23 13:27 eu.hlp
-rw-r--r-- 1 felix felix   1934 Apr 23 13:27 eu.tr
-rw-r--r-- 1 felix felix     53 Apr 23 13:27 exithelp.cfg
-rw-r--r-- 1 felix felix    723 Apr 23 13:27 f10.txt
-rw-r--r-- 1 felix felix    866 Apr 23 13:27 f1.txt
-rw-r--r-- 1 felix felix    739 Apr 23 13:27 f2.txt
-rw-r--r-- 1 felix felix    782 Apr 23 13:27 f3.txt
-rw-r--r-- 1 felix felix    417 Apr 23 13:27 f4.txt
-rw-r--r-- 1 felix felix    806 Apr 23 13:27 f5.txt
-rw-r--r-- 1 felix felix   1212 Apr 23 13:27 f6.txt
-rw-r--r-- 1 felix felix    916 Apr 23 13:27 f7.txt
-rw-r--r-- 1 felix felix   1051 Apr 23 13:27 f8.txt
-rw-r--r-- 1 felix felix    765 Apr 23 13:27 f9.txt
-rw-r--r-- 1 felix felix   2412 Apr 23 13:27 fa.tr
-rw-r--r-- 1 felix felix   7146 Apr 23 13:27 fi.hlp
-rw-r--r-- 1 felix felix   2007 Apr 23 13:27 fi.tr
-rw-r--r-- 1 felix felix   7967 Apr 23 13:27 fr.hlp
-rw-r--r-- 1 felix felix   2180 Apr 23 13:27 fr.tr
-rw-r--r-- 1 felix felix   2213 Apr 23 13:27 ga.tr
-rw-r--r-- 1 felix felix  21948 Apr 23 13:27 gfxboot.c32
-rw-r--r-- 1 felix felix    369 Apr 23 13:27 gfxboot.cfg
-rw-r--r-- 1 felix felix   7558 Apr 23 13:27 gl.hlp
-rw-r--r-- 1 felix felix   2025 Apr 23 13:27 gl.tr
-rw-r--r-- 1 felix felix   9393 Apr 23 13:27 he.hlp
-rw-r--r-- 1 felix felix   2884 Apr 23 13:27 he.tr
-rw-r--r-- 1 felix felix      0 Apr 23 13:27 hi.hlp
-rw-r--r-- 1 felix felix   2017 Apr 23 13:27 hr.tr
-rw-r--r-- 1 felix felix   7805 Apr 23 13:27 hu.hlp
-rw-r--r-- 1 felix felix   2340 Apr 23 13:27 hu.tr
-rw-r--r-- 1 felix felix   7086 Apr 23 13:27 id.hlp
-rw-r--r-- 1 felix felix   1780 Apr 23 13:27 id.tr
-rw-r--r-- 1 felix felix   7432 Apr 23 13:27 is.hlp
-rw-r--r-- 1 felix felix  24576 Apr 23 13:27 isolinux.bin
-rw-r--r-- 1 felix felix    103 Apr 23 13:27 isolinux.cfg
-rw-r--r-- 1 felix felix   2247 Apr 23 13:27 is.tr
-rw-r--r-- 1 felix felix   7132 Apr 23 13:27 it.hlp
-rw-r--r-- 1 felix felix   1997 Apr 23 13:27 it.tr
-rw-r--r-- 1 felix felix   9409 Apr 23 13:27 ja.hlp
-rw-r--r-- 1 felix felix   2936 Apr 23 13:27 ja.tr
-rw-r--r-- 1 felix felix  12434 Apr 23 13:27 ka.hlp
-rw-r--r-- 1 felix felix   4953 Apr 23 13:27 ka.tr
-rw-r--r-- 1 felix felix  13120 Apr 23 13:27 kk.hlp
-rw-r--r-- 1 felix felix   3721 Apr 23 13:27 kk.tr
-rw-r--r-- 1 felix felix  18608 Apr 23 13:27 km.hlp
-rw-r--r-- 1 felix felix   5387 Apr 23 13:27 kn.tr
-rw-r--r-- 1 felix felix   8260 Apr 23 13:27 ko.hlp
-rw-r--r-- 1 felix felix   2316 Apr 23 13:27 ko.tr
-rw-r--r-- 1 felix felix   2088 Apr 23 13:27 ku.tr
-rw-r--r-- 1 felix felix    226 Apr 23 13:27 langlist
-rw-r--r-- 1 felix felix   5251 Apr 23 13:27 lo.tr
-rw-r--r-- 1 felix felix   7324 Apr 23 13:27 lt.hlp
-rw-r--r-- 1 felix felix   2177 Apr 23 13:27 lt.tr
-rw-r--r-- 1 felix felix   7872 Apr 23 13:27 lv.hlp
-rw-r--r-- 1 felix felix   2170 Apr 23 13:27 lv.tr
-rw-r--r-- 1 felix felix    437 Apr 23 13:27 menu.cfg
-rw-r--r-- 1 felix felix   3371 Apr 23 13:27 mk.tr
-rw-r--r-- 1 felix felix   5278 Apr 23 13:27 mr.tr
-rw-r--r-- 1 felix felix   6962 Apr 23 13:27 nb.hlp
-rw-r--r-- 1 felix felix   1930 Apr 23 13:27 nb.tr
-rw-r--r-- 1 felix felix   7142 Apr 23 13:27 nl.hlp
-rw-r--r-- 1 felix felix   2172 Apr 23 13:27 nl.tr
-rw-r--r-- 1 felix felix   7214 Apr 23 13:27 nn.hlp
-rw-r--r-- 1 felix felix   1902 Apr 23 13:27 nn.tr
-rw-r--r-- 1 felix felix   7593 Apr 23 13:27 pl.hlp
-rw-r--r-- 1 felix felix   2190 Apr 23 13:27 pl.tr
-rw-r--r-- 1 felix felix    185 Apr 23 13:27 po4a.cfg
-rw-r--r-- 1 felix felix    175 Apr 23 13:27 prompt.cfg
-rw-r--r-- 1 felix felix   7453 Apr 23 13:27 pt_BR.hlp
-rw-r--r-- 1 felix felix   2195 Apr 23 13:27 pt_BR.tr
-rw-r--r-- 1 felix felix   7550 Apr 23 13:27 pt.hlp
-rw-r--r-- 1 felix felix   2138 Apr 23 13:27 pt.tr
-rw-r--r-- 1 felix felix   8630 Apr 23 13:27 ro.hlp
-rw-r--r-- 1 felix felix   2186 Apr 23 13:27 ro.tr
-rw-r--r-- 1 felix felix    134 Apr 23 13:27 rqtxt.cfg
-rw-r--r-- 1 felix felix  12081 Apr 23 13:27 ru.hlp
-rw-r--r-- 1 felix felix   3530 Apr 23 13:27 ru.tr
-rw-r--r-- 1 felix felix  13669 Apr 23 13:27 si.hlp
-rw-r--r-- 1 felix felix   5539 Apr 23 13:27 si.tr
-rw-r--r-- 1 felix felix   7565 Apr 23 13:27 sk.hlp
-rw-r--r-- 1 felix felix   2323 Apr 23 13:27 sk.tr
-rw-r--r-- 1 felix felix   6978 Apr 23 13:27 sl.hlp
-rw-r--r-- 1 felix felix   2022 Apr 23 13:27 sl.tr
-rw-r--r-- 1 felix felix  14160 Apr 23 13:27 splash.pcx
-rw-r--r-- 1 felix felix  17333 Apr 23 13:27 splash.png
-rw-r--r-- 1 felix felix   8029 Apr 23 13:27 sq.hlp
-rw-r--r-- 1 felix felix   2052 Apr 23 13:27 sq.tr
-rw-r--r-- 1 felix felix  11627 Apr 23 13:27 sr.hlp
-rw-r--r-- 1 felix felix   3675 Apr 23 13:27 sr.tr
-rw-r--r-- 1 felix felix    508 Apr 23 13:27 stdmenu.cfg
-rw-r--r-- 1 felix felix   7278 Apr 23 13:27 sv.hlp
-rw-r--r-- 1 felix felix   2030 Apr 23 13:27 sv.tr
-rw-r--r-- 1 felix felix   5659 Apr 23 13:27 te.tr
-rw-r--r-- 1 felix felix    656 Feb 14 11:51 text.cfg
-rw-r--r-- 1 felix felix  13110 Apr 23 13:27 th.hlp
-rw-r--r-- 1 felix felix   1806 Apr 23 13:27 tl.tr
-rw-r--r-- 1 felix felix   7761 Apr 23 13:27 tr.hlp
-rw-r--r-- 1 felix felix   2137 Apr 23 13:27 tr.tr
-rw-r--r-- 1 felix felix    656 Apr 23 13:27 txt.cfg
-rw-r--r-- 1 felix felix  11831 Apr 23 13:27 ug.hlp
-rw-r--r-- 1 felix felix  11766 Apr 23 13:27 uk.hlp
-rw-r--r-- 1 felix felix   3694 Apr 23 13:27 uk.tr
-rw-r--r-- 1 felix felix 155792 Apr 23 13:27 vesamenu.c32
-rw-r--r-- 1 felix felix   9735 Apr 23 13:27 vi.hlp
-rw-r--r-- 1 felix felix   2661 Apr 23 13:27 vi.tr
-rw-r--r-- 1 felix felix   6267 Apr 23 13:27 zh_CN.hlp
-rw-r--r-- 1 felix felix   1866 Apr 23 13:27 zh_CN.tr
-rw-r--r-- 1 felix felix   6222 Apr 23 13:27 zh_TW.hlp
-rw-r--r-- 1 felix felix   2008 Apr 23 13:27 zh_TW.tr

/media/U12~04~1k/pics:
total 48
-rw-r--r-- 1 felix felix  294 Apr 23 13:27 blue-lowerleft.png
-rw-r--r-- 1 felix felix  266 Apr 23 13:27 blue-lowerright.png
-rw-r--r-- 1 felix felix  280 Apr 23 13:27 blue-upperleft.png
-rw-r--r-- 1 felix felix  290 Apr 23 13:27 blue-upperright.png
-rw-r--r-- 1 felix felix 8442 Apr 23 13:27 debian.jpg
-rw-r--r-- 1 felix felix 3986 Apr 23 13:27 logo-50.jpg
-rw-r--r-- 1 felix felix  353 Apr 23 13:27 red-lowerleft.png
-rw-r--r-- 1 felix felix  299 Apr 23 13:27 red-lowerright.png
-rw-r--r-- 1 felix felix  321 Apr 23 13:27 red-upperleft.png
-rw-r--r-- 1 felix felix  344 Apr 23 13:27 red-upperright.png

/media/U12~04~1k/pool:
total 8
drwx------ 15 felix felix 4096 Jul 16 11:13 main
drwx------  4 felix felix 4096 Jul 16 10:31 restricted

/media/U12~04~1k/pool/main:
total 52
drwx------ 4 felix felix 4096 Jul 16 10:31 b
drwx------ 4 felix felix 4096 Jul 16 10:31 d
drwx------ 3 felix felix 4096 Jul 16 10:31 f
drwx------ 4 felix felix 4096 Jul 16 10:31 g
drwx------ 4 felix felix 4096 Jul 16 10:31 l
drwx------ 3 felix felix 4096 Jul 16 11:13 libg
drwx------ 3 felix felix 4096 Jul 16 10:31 m
drwx------ 4 felix felix 4096 Jul 16 10:31 n
drwx------ 4 felix felix 4096 Jul 16 11:13 p
drwx------ 3 felix felix 4096 Jul 16 10:31 s
drwx------ 5 felix felix 4096 Jul 16 11:13 u
drwx------ 4 felix felix 4096 Jul 16 10:31 w
drwx------ 3 felix felix 4096 Jul 16 10:31 x

/media/U12~04~1k/pool/main/b:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 b43-fwcutter
drwx------ 2 felix felix 4096 Jul 16 10:34 build-essential

/media/U12~04~1k/pool/main/b/b43-fwcutter:
total 40
-rw-r--r-- 1 felix felix 17886 Mar  6  2010 b43-fwcutter_012-1build1_i386.deb
-rw-r--r-- 1 felix felix 18866 Apr 23 13:27 b43-fwcutter_015-9_i386.deb

/media/U12~04~1k/pool/main/b/build-essential:
total 8
-rw-r--r-- 1 felix felix 7278 Mar  6  2010 build-essential_11.4build1_i386.deb

/media/U12~04~1k/pool/main/d:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 dkms
drwx------ 2 felix felix 4096 Jul 16 10:34 dpkg

/media/U12~04~1k/pool/main/d/dkms:
total 144
-rw-r--r-- 1 felix felix 70836 Jun  9  2011 dkms_2.1.1.2-2ubuntu1_all.deb
-rw-r--r-- 1 felix felix 73066 Apr 23 13:27 dkms_2.2.0.3-1ubuntu3_all.deb

/media/U12~04~1k/pool/main/d/dpkg:
total 640
-rw-r--r-- 1 felix felix 653864 Jan  6  2011 dpkg-dev_1.15.5.6ubuntu4.5_all.deb

/media/U12~04~1k/pool/main/f:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 fakeroot

/media/U12~04~1k/pool/main/f/fakeroot:
total 204
-rw-r--r-- 1 felix felix 117500 Jan  8  2010 fakeroot_1.14.4-1ubuntu1_i386.deb
-rw-r--r-- 1 felix felix  87928 Apr 23 13:27 fakeroot_1.18.2-1_i386.deb

/media/U12~04~1k/pool/main/g:
total 8
drwx------ 2 felix felix 4096 Jul 16 10:34 gcc-4.4
drwx------ 2 felix felix 4096 Jul 16 10:34 gcc-defaults

/media/U12~04~1k/pool/main/g/gcc-4.4:
total 6296
-rw-r--r-- 1 felix felix 4949970 Mar 26  2010 g++-4.4_4.4.3-4ubuntu5_i386.deb
-rw-r--r-- 1 felix felix 1491106 Mar 26  2010 libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb

/media/U12~04~1k/pool/main/g/gcc-defaults:
total 4
-rw-r--r-- 1 felix felix 1442 Mar 19  2010 g++_4.4.3-1ubuntu1_i386.deb

/media/U12~04~1k/pool/main/l:
total 8
drwx------ 2 felix felix 4096 Jul 16 10:34 linux-wlan-ng
drwx------ 2 felix felix 4096 Jul 16 11:17 lupin

/media/U12~04~1k/pool/main/l/linux-wlan-ng:
total 196
-rw-r--r-- 1 felix felix 110276 Feb 22  2010 linux-wlan-ng_0.2.9+dfsg-4_i386.deb
-rw-r--r-- 1 felix felix  88148 Feb 22  2010 linux-wlan-ng-doc_0.2.9+dfsg-4_all.deb

/media/U12~04~1k/pool/main/l/lupin:
total 32
-rw-r--r-- 1 felix felix 12732 Jun  6  2011 lupin-support_0.29.1_i386.deb
-rw-r--r-- 1 felix felix 13048 Apr 23 13:27 lupin-support_0.51_i386.deb

/media/U12~04~1k/pool/main/libg:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 libglade2

/media/U12~04~1k/pool/main/libg/libglade2:
total 52
-rw-r--r-- 1 felix felix 52446 Apr 23 13:27 libglade2-0_2.6.4-1ubuntu1_i386.deb

/media/U12~04~1k/pool/main/m:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 mouseemu

/media/U12~04~1k/pool/main/m/mouseemu:
total 40
-rw-r--r-- 1 felix felix 18522 Mar 31  2010 mouseemu_0.16-0ubuntu6_i386.deb
-rw-r--r-- 1 felix felix 18442 Apr 23 13:27 mouseemu_0.16-0ubuntu7_i386.deb

/media/U12~04~1k/pool/main/n:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 ndisgtk
drwx------ 2 felix felix 4096 Jul 16 11:17 ndiswrapper

/media/U12~04~1k/pool/main/n/ndisgtk:
total 24
-rw-r--r-- 1 felix felix 21354 Apr 23 13:27 ndisgtk_0.8.5-1_i386.deb

/media/U12~04~1k/pool/main/n/ndiswrapper:
total 92
-rw-r--r-- 1 felix felix 21668 Apr 30  2009 ndiswrapper-common_1.54-2ubuntu1_all.deb
-rw-r--r-- 1 felix felix  5988 Apr 23 13:27 ndiswrapper-common_1.57-1ubuntu1_all.deb
-rw-r--r-- 1 felix felix 36464 Apr 30  2009 ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb
-rw-r--r-- 1 felix felix 20934 Apr 23 13:27 ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb

/media/U12~04~1k/pool/main/p:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 patch
drwx------ 2 felix felix 4096 Jul 16 11:17 pygtk

/media/U12~04~1k/pool/main/p/patch:
total 212
-rw-r--r-- 1 felix felix  86020 Apr 23 13:27 patch_2.6.1-3_i386.deb
-rw-r--r-- 1 felix felix 122946 Apr  5  2010 patch_2.6-2ubuntu1_i386.deb

/media/U12~04~1k/pool/main/p/pygtk:
total 12
-rw-r--r-- 1 felix felix 9870 Apr 23 13:27 python-glade2_2.24.0-3_i386.deb

/media/U12~04~1k/pool/main/s:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 setserial

/media/U12~04~1k/pool/main/s/setserial:
total 92
-rw-r--r-- 1 felix felix 52404 Jan 19  2010 setserial_2.17-45.2_i386.deb
-rw-r--r-- 1 felix felix 40096 Apr 23 13:27 setserial_2.17-46_i386.deb

/media/U12~04~1k/pool/main/u:
total 12
drwx------ 2 felix felix 4096 Jul 16 11:17 ubiquity
drwx------ 2 felix felix 4096 Jul 16 11:17 ubiquity-slideshow-ubuntu
drwx------ 2 felix felix 4096 Jul 16 11:17 user-setup

/media/U12~04~1k/pool/main/u/ubiquity:
total 240
-rw-r--r-- 1 felix felix  14538 Apr 23 13:27 oem-config_2.10.16_all.deb
-rw-r--r-- 1 felix felix 113120 Jul 18  2011 oem-config_2.2.27_all.deb
-rw-r--r-- 1 felix felix   4188 Apr 23 13:27 oem-config-gtk_2.10.16_all.deb
-rw-r--r-- 1 felix felix 105176 Jul 18  2011 oem-config-gtk_2.2.27_all.deb

/media/U12~04~1k/pool/main/u/ubiquity-slideshow-ubuntu:
total 720
-rw-r--r-- 1 felix felix 734798 Apr 23 13:27 oem-config-slideshow-ubuntu_58_all.deb

/media/U12~04~1k/pool/main/u/user-setup:
total 184
-rw-r--r-- 1 felix felix 187908 Apr 23 13:27 user-setup_1.42ubuntu3_all.deb

/media/U12~04~1k/pool/main/w:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 wvdial
drwx------ 2 felix felix 4096 Jul 16 11:17 wvstreams

/media/U12~04~1k/pool/main/w/wvdial:
total 256
-rw-r--r-- 1 felix felix 174596 Jan 11  2010 wvdial_1.60.3_i386.deb
-rw-r--r-- 1 felix felix  85876 Apr 23 13:27 wvdial_1.61-4build1_i386.deb

/media/U12~04~1k/pool/main/w/wvstreams:
total 1672
-rw-r--r-- 1 felix felix 183292 Jan  5  2010 libuniconf4.6_4.6.1-1_i386.deb
-rw-r--r-- 1 felix felix 125798 Apr 23 13:27 libuniconf4.6_4.6.1-2build1_i386.deb
-rw-r--r-- 1 felix felix 258602 Jan  5  2010 libwvstreams4.6-base_4.6.1-1_i386.deb
-rw-r--r-- 1 felix felix 201994 Apr 23 13:27 libwvstreams4.6-base_4.6.1-2build1_i386.deb
-rw-r--r-- 1 felix felix 490454 Jan  5  2010 libwvstreams4.6-extras_4.6.1-1_i386.deb
-rw-r--r-- 1 felix felix 441166 Apr 23 13:27 libwvstreams4.6-extras_4.6.1-2build1_i386.deb

/media/U12~04~1k/pool/main/x:
total 4
drwx------ 2 felix felix 4096 Jul 16 10:34 xz-utils

/media/U12~04~1k/pool/main/x/xz-utils:
total 224
-rw-r--r-- 1 felix felix 228052 Dec 22  2009 xz-utils_4.999.9beta+20091116-1_i386.deb

/media/U12~04~1k/pool/restricted:
total 8
drwx------ 3 felix felix 4096 Jul 16 10:31 b
drwx------ 3 felix felix 4096 Jul 16 10:31 s

/media/U12~04~1k/pool/restricted/b:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 bcmwl

/media/U12~04~1k/pool/restricted/b/bcmwl:
total 2052
-rw-r--r-- 1 felix felix 1202502 Apr 23 13:27 bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_i386.deb
-rw-r--r-- 1 felix felix  894608 Apr 22  2010 bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb

/media/U12~04~1k/pool/restricted/s:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 sl-modem

/media/U12~04~1k/pool/restricted/s/sl-modem:
total 1012
-rw-r--r-- 1 felix felix 517564 Mar 23  2010 sl-modem-daemon_2.9.11~20100303-2_i386.deb
-rw-r--r-- 1 felix felix 512656 Apr 23 13:27 sl-modem-daemon_2.9.11~20110321-6_i386.deb

/media/U12~04~1k/preseed:
total 12
-rw-r--r-- 1 felix felix 212 Apr 23 13:27 cli.seed
-rw-r--r-- 1 felix felix 497 Apr 23 13:27 ltsp.seed
-rw-r--r-- 1 felix felix 460 Apr 23 13:27 ubuntu.seed
felix@emma:~$ 
felix@emma:~$ 
felix@emma:~$ 
felix@emma:~$ ls -l -R /media/u10.04
/media/u10.04:
total 226836
-rw-r--r-- 1 felix felix       134 Apr 23 13:27 autorun.inf
drwx------ 3 felix felix      4096 Jul 16 11:13 boot
drwx------ 2 felix felix      4096 Jul 16 11:46 casper
-rw-r--r-- 1 felix felix 209715200 Jul 16 12:53 casper-rw
drwx------ 4 felix felix      4096 Jul 16 11:13 dists
drwx------ 2 felix felix      4096 Jul 16 11:17 install
drwx------ 2 felix felix     12288 Jul 16 11:17 isolinux
-r--r--r-- 1 felix felix     32768 Jul 16 11:17 ldlinux.sys
-rw-r--r-- 1 felix felix      4237 Apr 23 13:27 md5sum.txt
-rw-r--r-- 1 felix felix     60928 Jul 16 11:17 menu.c32
drwx------ 2 felix felix      4096 Jul 16 11:17 pics
drwx------ 4 felix felix      4096 Jul 16 10:31 pool
drwx------ 2 felix felix      4096 Jul 16 11:17 preseed
-rw-r--r-- 1 felix felix       231 Apr 23 13:27 README.diskdefines
-rw-r--r-- 1 felix felix      1041 Jul 16 11:17 syslinux.cfg
-rw-r--r-- 1 felix felix      4478 Jul 16 11:17 ubnfilel.txt
-rw-r--r-- 1 felix felix  14873857 Apr 23 13:27 ubninit
-rw-r--r-- 1 felix felix   5015840 Apr 23 13:27 ubnkern
-rw-r--r-- 1 felix felix       318 Jul 16 11:13 ubnpathl.txt
-rw-r--r-- 1 felix felix         0 Feb 14 11:51 ubuntu
-rwxr-xr-x 1 felix felix   2502608 Apr 23 13:27 wubi.exe

/media/u10.04/boot:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:13 grub

/media/u10.04/boot/grub:
total 4
-rw-r--r-- 1 felix felix 589 Apr 23 13:27 loopback.cfg

/media/u10.04/casper:
total 708076
-rw-r--r-- 1 felix felix     41315 Apr 23 13:27 filesystem.manifest
-rw-r--r-- 1 felix felix     38275 Feb 14 10:48 filesystem.manifest-desktop
-rw-r--r-- 1 felix felix      1079 Apr 23 13:27 filesystem.manifest-remove
-rw-r--r-- 1 felix felix        11 Apr 23 13:27 filesystem.size
-rw-r--r-- 1 felix felix 704692224 Apr 23 13:27 filesystem.squashfs
-rw-r--r-- 1 felix felix  15263318 Jul 16 11:46 initrd.lz
-rw-r--r-- 1 felix felix   5015840 Apr 23 13:27 vmlinuz

/media/u10.04/dists:
total 8
drwx------ 4 felix felix 4096 Jul 16 10:34 lucid
drwx------ 4 felix felix 4096 Jul 16 11:17 precise
-rw-r--r-- 1 felix felix    0 Feb 14 11:51 stable
-rw-r--r-- 1 felix felix    0 Feb 14 11:51 unstable

/media/u10.04/dists/lucid:
total 16
drwx------ 4 felix felix 4096 Jul 16 10:31 main
-rw-r--r-- 1 felix felix 1759 Feb 14 11:51 Release
-rw-r--r-- 1 felix felix  198 Feb 14 11:51 Release.gpg
drwx------ 4 felix felix 4096 Jul 16 10:31 restricted

/media/u10.04/dists/lucid/main:
total 8
drwx------ 2 felix felix 4096 Jul 16 10:34 binary-i386
drwx------ 2 felix felix 4096 Jul 16 10:31 source

/media/u10.04/dists/lucid/main/binary-i386:
total 16
-rw-r--r-- 1 felix felix 9400 Feb 14 11:51 Packages.gz
-rw-r--r-- 1 felix felix   94 Feb 14 11:51 Release

/media/u10.04/dists/lucid/main/source:
total 0

/media/u10.04/dists/lucid/restricted:
total 8
drwx------ 2 felix felix 4096 Jul 16 10:34 binary-i386
drwx------ 2 felix felix 4096 Jul 16 10:31 source

/media/u10.04/dists/lucid/restricted/binary-i386:
total 8
-rw-r--r-- 1 felix felix 1270 Feb 14 11:51 Packages.gz
-rw-r--r-- 1 felix felix  100 Feb 14 11:51 Release

/media/u10.04/dists/lucid/restricted/source:
total 0

/media/u10.04/dists/precise:
total 16
drwx------ 4 felix felix 4096 Jul 16 11:13 main
-rw-r--r-- 1 felix felix 1765 Apr 23 13:27 Release
-rw-r--r-- 1 felix felix  198 Apr 23 13:27 Release.gpg
drwx------ 4 felix felix 4096 Jul 16 11:13 restricted

/media/u10.04/dists/precise/main:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 binary-i386
drwx------ 2 felix felix 4096 Jul 16 11:13 source

/media/u10.04/dists/precise/main/binary-i386:
total 12
-rw-r--r-- 1 felix felix 7427 Apr 23 13:27 Packages.gz
-rw-r--r-- 1 felix felix   96 Apr 23 13:27 Release

/media/u10.04/dists/precise/main/source:
total 0

/media/u10.04/dists/precise/restricted:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 binary-i386
drwx------ 2 felix felix 4096 Jul 16 11:13 source

/media/u10.04/dists/precise/restricted/binary-i386:
total 8
-rw-r--r-- 1 felix felix 1406 Apr 23 13:27 Packages.gz
-rw-r--r-- 1 felix felix  102 Apr 23 13:27 Release

/media/u10.04/dists/precise/restricted/source:
total 0

/media/u10.04/install:
total 1620
-rw-r--r-- 1 felix felix  176764 Apr 23 13:27 mt86plus
-rw-r--r-- 1 felix felix    1865 Apr 23 13:27 README.sbm
-rw-r--r-- 1 felix felix 1474560 Apr 23 13:27 sbm.bin

/media/u10.04/isolinux:
total 1328
-rw-r--r-- 1 felix felix  71280 Apr 23 13:27 16x16.fnt
-rw-r--r-- 1 felix felix   3404 Apr 23 13:27 access.pcx
-rw-r--r-- 1 felix felix      0 Feb 14 11:51 adtext.cfg
-rw-r--r-- 1 felix felix      0 Apr 23 13:27 adtxt.cfg
-rw-r--r-- 1 felix felix   2967 Apr 23 13:27 am.tr
-rw-r--r-- 1 felix felix   7340 Apr 23 13:27 ast.hlp
-rw-r--r-- 1 felix felix   2007 Apr 23 13:27 ast.tr
-rw-r--r-- 1 felix felix   7500 Apr 23 13:27 back.jpg
-rw-r--r-- 1 felix felix  11711 Apr 23 13:27 be.hlp
-rw-r--r-- 1 felix felix   3483 Apr 23 13:27 be.tr
-rw-r--r-- 1 felix felix  11704 Apr 23 13:27 bg.hlp
-rw-r--r-- 1 felix felix   3869 Apr 23 13:27 bg.tr
-rw-r--r-- 1 felix felix  11457 Apr 23 13:27 blank.pcx
-rw-r--r-- 1 felix felix  15128 Apr 23 13:27 bn.hlp
-rw-r--r-- 1 felix felix   2048 Apr 23 13:27 boot.cat
-rw-r--r-- 1 felix felix 108032 Apr 23 13:27 bootlogo
-rw-r--r-- 1 felix felix   7082 Apr 23 13:27 bs.hlp
-rw-r--r-- 1 felix felix   1950 Apr 23 13:27 bs.tr
-rw-r--r-- 1 felix felix   8050 Apr 23 13:27 ca.hlp
-rw-r--r-- 1 felix felix   2243 Apr 23 13:27 ca.tr
-rw-r--r-- 1 felix felix  20704 Apr 23 13:27 chain.c32
-rw-r--r-- 1 felix felix   7383 Apr 23 13:27 cs.hlp
-rw-r--r-- 1 felix felix   2135 Apr 23 13:27 cs.tr
-rw-r--r-- 1 felix felix   6907 Apr 23 13:27 da.hlp
-rw-r--r-- 1 felix felix   1971 Apr 23 13:27 da.tr
-rw-r--r-- 1 felix felix   7749 Apr 23 13:27 de.hlp
-rw-r--r-- 1 felix felix   2196 Apr 23 13:27 de.tr
-rw-r--r-- 1 felix felix   1423 Apr 23 13:27 dtmenu.cfg
-rw-r--r-- 1 felix felix  13417 Apr 23 13:27 el.hlp
-rw-r--r-- 1 felix felix   4061 Apr 23 13:27 el.tr
-rw-r--r-- 1 felix felix   6501 Apr 23 13:27 en.hlp
-rw-r--r-- 1 felix felix   1759 Apr 23 13:27 en.tr
-rw-r--r-- 1 felix felix   6874 Apr 23 13:27 eo.hlp
-rw-r--r-- 1 felix felix   1928 Apr 23 13:27 eo.tr
-rw-r--r-- 1 felix felix   7586 Apr 23 13:27 es.hlp
-rw-r--r-- 1 felix felix   2037 Apr 23 13:27 es.tr
-rw-r--r-- 1 felix felix   6742 Apr 23 13:27 et.hlp
-rw-r--r-- 1 felix felix   1895 Apr 23 13:27 et.tr
-rw-r--r-- 1 felix felix   7173 Apr 23 13:27 eu.hlp
-rw-r--r-- 1 felix felix   1934 Apr 23 13:27 eu.tr
-rw-r--r-- 1 felix felix     53 Apr 23 13:27 exithelp.cfg
-rw-r--r-- 1 felix felix    723 Apr 23 13:27 f10.txt
-rw-r--r-- 1 felix felix    866 Apr 23 13:27 f1.txt
-rw-r--r-- 1 felix felix    739 Apr 23 13:27 f2.txt
-rw-r--r-- 1 felix felix    782 Apr 23 13:27 f3.txt
-rw-r--r-- 1 felix felix    417 Apr 23 13:27 f4.txt
-rw-r--r-- 1 felix felix    806 Apr 23 13:27 f5.txt
-rw-r--r-- 1 felix felix   1212 Apr 23 13:27 f6.txt
-rw-r--r-- 1 felix felix    916 Apr 23 13:27 f7.txt
-rw-r--r-- 1 felix felix   1051 Apr 23 13:27 f8.txt
-rw-r--r-- 1 felix felix    765 Apr 23 13:27 f9.txt
-rw-r--r-- 1 felix felix   2412 Apr 23 13:27 fa.tr
-rw-r--r-- 1 felix felix   7146 Apr 23 13:27 fi.hlp
-rw-r--r-- 1 felix felix   2007 Apr 23 13:27 fi.tr
-rw-r--r-- 1 felix felix   7967 Apr 23 13:27 fr.hlp
-rw-r--r-- 1 felix felix   2180 Apr 23 13:27 fr.tr
-rw-r--r-- 1 felix felix   2213 Apr 23 13:27 ga.tr
-rw-r--r-- 1 felix felix  21948 Apr 23 13:27 gfxboot.c32
-rw-r--r-- 1 felix felix    369 Apr 23 13:27 gfxboot.cfg
-rw-r--r-- 1 felix felix   7558 Apr 23 13:27 gl.hlp
-rw-r--r-- 1 felix felix   2025 Apr 23 13:27 gl.tr
-rw-r--r-- 1 felix felix   9393 Apr 23 13:27 he.hlp
-rw-r--r-- 1 felix felix   2884 Apr 23 13:27 he.tr
-rw-r--r-- 1 felix felix      0 Apr 23 13:27 hi.hlp
-rw-r--r-- 1 felix felix   2017 Apr 23 13:27 hr.tr
-rw-r--r-- 1 felix felix   7805 Apr 23 13:27 hu.hlp
-rw-r--r-- 1 felix felix   2340 Apr 23 13:27 hu.tr
-rw-r--r-- 1 felix felix   7086 Apr 23 13:27 id.hlp
-rw-r--r-- 1 felix felix   1780 Apr 23 13:27 id.tr
-rw-r--r-- 1 felix felix   7432 Apr 23 13:27 is.hlp
-rw-r--r-- 1 felix felix  24576 Apr 23 13:27 isolinux.bin
-rw-r--r-- 1 felix felix    103 Apr 23 13:27 isolinux.cfg
-rw-r--r-- 1 felix felix   2247 Apr 23 13:27 is.tr
-rw-r--r-- 1 felix felix   7132 Apr 23 13:27 it.hlp
-rw-r--r-- 1 felix felix   1997 Apr 23 13:27 it.tr
-rw-r--r-- 1 felix felix   9409 Apr 23 13:27 ja.hlp
-rw-r--r-- 1 felix felix   2936 Apr 23 13:27 ja.tr
-rw-r--r-- 1 felix felix  12434 Apr 23 13:27 ka.hlp
-rw-r--r-- 1 felix felix   4953 Apr 23 13:27 ka.tr
-rw-r--r-- 1 felix felix  13120 Apr 23 13:27 kk.hlp
-rw-r--r-- 1 felix felix   3721 Apr 23 13:27 kk.tr
-rw-r--r-- 1 felix felix  18608 Apr 23 13:27 km.hlp
-rw-r--r-- 1 felix felix   5387 Apr 23 13:27 kn.tr
-rw-r--r-- 1 felix felix   8260 Apr 23 13:27 ko.hlp
-rw-r--r-- 1 felix felix   2316 Apr 23 13:27 ko.tr
-rw-r--r-- 1 felix felix   2088 Apr 23 13:27 ku.tr
-rw-r--r-- 1 felix felix    226 Apr 23 13:27 langlist
-rw-r--r-- 1 felix felix   5251 Apr 23 13:27 lo.tr
-rw-r--r-- 1 felix felix   7324 Apr 23 13:27 lt.hlp
-rw-r--r-- 1 felix felix   2177 Apr 23 13:27 lt.tr
-rw-r--r-- 1 felix felix   7872 Apr 23 13:27 lv.hlp
-rw-r--r-- 1 felix felix   2170 Apr 23 13:27 lv.tr
-rw-r--r-- 1 felix felix    437 Apr 23 13:27 menu.cfg
-rw-r--r-- 1 felix felix   3371 Apr 23 13:27 mk.tr
-rw-r--r-- 1 felix felix   5278 Apr 23 13:27 mr.tr
-rw-r--r-- 1 felix felix   6962 Apr 23 13:27 nb.hlp
-rw-r--r-- 1 felix felix   1930 Apr 23 13:27 nb.tr
-rw-r--r-- 1 felix felix   7142 Apr 23 13:27 nl.hlp
-rw-r--r-- 1 felix felix   2172 Apr 23 13:27 nl.tr
-rw-r--r-- 1 felix felix   7214 Apr 23 13:27 nn.hlp
-rw-r--r-- 1 felix felix   1902 Apr 23 13:27 nn.tr
-rw-r--r-- 1 felix felix   7593 Apr 23 13:27 pl.hlp
-rw-r--r-- 1 felix felix   2190 Apr 23 13:27 pl.tr
-rw-r--r-- 1 felix felix    185 Apr 23 13:27 po4a.cfg
-rw-r--r-- 1 felix felix    175 Apr 23 13:27 prompt.cfg
-rw-r--r-- 1 felix felix   7453 Apr 23 13:27 pt_BR.hlp
-rw-r--r-- 1 felix felix   2195 Apr 23 13:27 pt_BR.tr
-rw-r--r-- 1 felix felix   7550 Apr 23 13:27 pt.hlp
-rw-r--r-- 1 felix felix   2138 Apr 23 13:27 pt.tr
-rw-r--r-- 1 felix felix   8630 Apr 23 13:27 ro.hlp
-rw-r--r-- 1 felix felix   2186 Apr 23 13:27 ro.tr
-rw-r--r-- 1 felix felix    134 Apr 23 13:27 rqtxt.cfg
-rw-r--r-- 1 felix felix  12081 Apr 23 13:27 ru.hlp
-rw-r--r-- 1 felix felix   3530 Apr 23 13:27 ru.tr
-rw-r--r-- 1 felix felix  13669 Apr 23 13:27 si.hlp
-rw-r--r-- 1 felix felix   5539 Apr 23 13:27 si.tr
-rw-r--r-- 1 felix felix   7565 Apr 23 13:27 sk.hlp
-rw-r--r-- 1 felix felix   2323 Apr 23 13:27 sk.tr
-rw-r--r-- 1 felix felix   6978 Apr 23 13:27 sl.hlp
-rw-r--r-- 1 felix felix   2022 Apr 23 13:27 sl.tr
-rw-r--r-- 1 felix felix  14160 Apr 23 13:27 splash.pcx
-rw-r--r-- 1 felix felix  17333 Apr 23 13:27 splash.png
-rw-r--r-- 1 felix felix   8029 Apr 23 13:27 sq.hlp
-rw-r--r-- 1 felix felix   2052 Apr 23 13:27 sq.tr
-rw-r--r-- 1 felix felix  11627 Apr 23 13:27 sr.hlp
-rw-r--r-- 1 felix felix   3675 Apr 23 13:27 sr.tr
-rw-r--r-- 1 felix felix    508 Apr 23 13:27 stdmenu.cfg
-rw-r--r-- 1 felix felix   7278 Apr 23 13:27 sv.hlp
-rw-r--r-- 1 felix felix   2030 Apr 23 13:27 sv.tr
-rw-r--r-- 1 felix felix   5659 Apr 23 13:27 te.tr
-rw-r--r-- 1 felix felix    656 Feb 14 11:51 text.cfg
-rw-r--r-- 1 felix felix  13110 Apr 23 13:27 th.hlp
-rw-r--r-- 1 felix felix   1806 Apr 23 13:27 tl.tr
-rw-r--r-- 1 felix felix   7761 Apr 23 13:27 tr.hlp
-rw-r--r-- 1 felix felix   2137 Apr 23 13:27 tr.tr
-rw-r--r-- 1 felix felix    656 Apr 23 13:27 txt.cfg
-rw-r--r-- 1 felix felix  11831 Apr 23 13:27 ug.hlp
-rw-r--r-- 1 felix felix  11766 Apr 23 13:27 uk.hlp
-rw-r--r-- 1 felix felix   3694 Apr 23 13:27 uk.tr
-rw-r--r-- 1 felix felix 155792 Apr 23 13:27 vesamenu.c32
-rw-r--r-- 1 felix felix   9735 Apr 23 13:27 vi.hlp
-rw-r--r-- 1 felix felix   2661 Apr 23 13:27 vi.tr
-rw-r--r-- 1 felix felix   6267 Apr 23 13:27 zh_CN.hlp
-rw-r--r-- 1 felix felix   1866 Apr 23 13:27 zh_CN.tr
-rw-r--r-- 1 felix felix   6222 Apr 23 13:27 zh_TW.hlp
-rw-r--r-- 1 felix felix   2008 Apr 23 13:27 zh_TW.tr

/media/u10.04/pics:
total 48
-rw-r--r-- 1 felix felix  294 Apr 23 13:27 blue-lowerleft.png
-rw-r--r-- 1 felix felix  266 Apr 23 13:27 blue-lowerright.png
-rw-r--r-- 1 felix felix  280 Apr 23 13:27 blue-upperleft.png
-rw-r--r-- 1 felix felix  290 Apr 23 13:27 blue-upperright.png
-rw-r--r-- 1 felix felix 8442 Apr 23 13:27 debian.jpg
-rw-r--r-- 1 felix felix 3986 Apr 23 13:27 logo-50.jpg
-rw-r--r-- 1 felix felix  353 Apr 23 13:27 red-lowerleft.png
-rw-r--r-- 1 felix felix  299 Apr 23 13:27 red-lowerright.png
-rw-r--r-- 1 felix felix  321 Apr 23 13:27 red-upperleft.png
-rw-r--r-- 1 felix felix  344 Apr 23 13:27 red-upperright.png

/media/u10.04/pool:
total 8
drwx------ 15 felix felix 4096 Jul 16 11:13 main
drwx------  4 felix felix 4096 Jul 16 10:31 restricted

/media/u10.04/pool/main:
total 52
drwx------ 4 felix felix 4096 Jul 16 10:31 b
drwx------ 4 felix felix 4096 Jul 16 10:31 d
drwx------ 3 felix felix 4096 Jul 16 10:31 f
drwx------ 4 felix felix 4096 Jul 16 10:31 g
drwx------ 4 felix felix 4096 Jul 16 10:31 l
drwx------ 3 felix felix 4096 Jul 16 11:13 libg
drwx------ 3 felix felix 4096 Jul 16 10:31 m
drwx------ 4 felix felix 4096 Jul 16 10:31 n
drwx------ 4 felix felix 4096 Jul 16 11:13 p
drwx------ 3 felix felix 4096 Jul 16 10:31 s
drwx------ 5 felix felix 4096 Jul 16 11:13 u
drwx------ 4 felix felix 4096 Jul 16 10:31 w
drwx------ 3 felix felix 4096 Jul 16 10:31 x

/media/u10.04/pool/main/b:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 b43-fwcutter
drwx------ 2 felix felix 4096 Jul 16 10:34 build-essential

/media/u10.04/pool/main/b/b43-fwcutter:
total 40
-rw-r--r-- 1 felix felix 17886 Mar  6  2010 b43-fwcutter_012-1build1_i386.deb
-rw-r--r-- 1 felix felix 18866 Apr 23 13:27 b43-fwcutter_015-9_i386.deb

/media/u10.04/pool/main/b/build-essential:
total 8
-rw-r--r-- 1 felix felix 7278 Mar  6  2010 build-essential_11.4build1_i386.deb

/media/u10.04/pool/main/d:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 dkms
drwx------ 2 felix felix 4096 Jul 16 10:34 dpkg

/media/u10.04/pool/main/d/dkms:
total 144
-rw-r--r-- 1 felix felix 70836 Jun  9  2011 dkms_2.1.1.2-2ubuntu1_all.deb
-rw-r--r-- 1 felix felix 73066 Apr 23 13:27 dkms_2.2.0.3-1ubuntu3_all.deb

/media/u10.04/pool/main/d/dpkg:
total 640
-rw-r--r-- 1 felix felix 653864 Jan  6  2011 dpkg-dev_1.15.5.6ubuntu4.5_all.deb

/media/u10.04/pool/main/f:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 fakeroot

/media/u10.04/pool/main/f/fakeroot:
total 204
-rw-r--r-- 1 felix felix 117500 Jan  8  2010 fakeroot_1.14.4-1ubuntu1_i386.deb
-rw-r--r-- 1 felix felix  87928 Apr 23 13:27 fakeroot_1.18.2-1_i386.deb

/media/u10.04/pool/main/g:
total 8
drwx------ 2 felix felix 4096 Jul 16 10:34 gcc-4.4
drwx------ 2 felix felix 4096 Jul 16 10:34 gcc-defaults

/media/u10.04/pool/main/g/gcc-4.4:
total 6296
-rw-r--r-- 1 felix felix 4949970 Mar 26  2010 g++-4.4_4.4.3-4ubuntu5_i386.deb
-rw-r--r-- 1 felix felix 1491106 Mar 26  2010 libstdc++6-4.4-dev_4.4.3-4ubuntu5_i386.deb

/media/u10.04/pool/main/g/gcc-defaults:
total 4
-rw-r--r-- 1 felix felix 1442 Mar 19  2010 g++_4.4.3-1ubuntu1_i386.deb

/media/u10.04/pool/main/l:
total 8
drwx------ 2 felix felix 4096 Jul 16 10:34 linux-wlan-ng
drwx------ 2 felix felix 4096 Jul 16 11:17 lupin

/media/u10.04/pool/main/l/linux-wlan-ng:
total 196
-rw-r--r-- 1 felix felix 110276 Feb 22  2010 linux-wlan-ng_0.2.9+dfsg-4_i386.deb
-rw-r--r-- 1 felix felix  88148 Feb 22  2010 linux-wlan-ng-doc_0.2.9+dfsg-4_all.deb

/media/u10.04/pool/main/l/lupin:
total 32
-rw-r--r-- 1 felix felix 12732 Jun  6  2011 lupin-support_0.29.1_i386.deb
-rw-r--r-- 1 felix felix 13048 Apr 23 13:27 lupin-support_0.51_i386.deb

/media/u10.04/pool/main/libg:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 libglade2

/media/u10.04/pool/main/libg/libglade2:
total 52
-rw-r--r-- 1 felix felix 52446 Apr 23 13:27 libglade2-0_2.6.4-1ubuntu1_i386.deb

/media/u10.04/pool/main/m:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 mouseemu

/media/u10.04/pool/main/m/mouseemu:
total 40
-rw-r--r-- 1 felix felix 18522 Mar 31  2010 mouseemu_0.16-0ubuntu6_i386.deb
-rw-r--r-- 1 felix felix 18442 Apr 23 13:27 mouseemu_0.16-0ubuntu7_i386.deb

/media/u10.04/pool/main/n:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 ndisgtk
drwx------ 2 felix felix 4096 Jul 16 11:17 ndiswrapper

/media/u10.04/pool/main/n/ndisgtk:
total 24
-rw-r--r-- 1 felix felix 21354 Apr 23 13:27 ndisgtk_0.8.5-1_i386.deb

/media/u10.04/pool/main/n/ndiswrapper:
total 92
-rw-r--r-- 1 felix felix 21668 Apr 30  2009 ndiswrapper-common_1.54-2ubuntu1_all.deb
-rw-r--r-- 1 felix felix  5988 Apr 23 13:27 ndiswrapper-common_1.57-1ubuntu1_all.deb
-rw-r--r-- 1 felix felix 36464 Apr 30  2009 ndiswrapper-utils-1.9_1.54-2ubuntu1_i386.deb
-rw-r--r-- 1 felix felix 20934 Apr 23 13:27 ndiswrapper-utils-1.9_1.57-1ubuntu1_i386.deb

/media/u10.04/pool/main/p:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 patch
drwx------ 2 felix felix 4096 Jul 16 11:17 pygtk

/media/u10.04/pool/main/p/patch:
total 212
-rw-r--r-- 1 felix felix  86020 Apr 23 13:27 patch_2.6.1-3_i386.deb
-rw-r--r-- 1 felix felix 122946 Apr  5  2010 patch_2.6-2ubuntu1_i386.deb

/media/u10.04/pool/main/p/pygtk:
total 12
-rw-r--r-- 1 felix felix 9870 Apr 23 13:27 python-glade2_2.24.0-3_i386.deb

/media/u10.04/pool/main/s:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 setserial

/media/u10.04/pool/main/s/setserial:
total 92
-rw-r--r-- 1 felix felix 52404 Jan 19  2010 setserial_2.17-45.2_i386.deb
-rw-r--r-- 1 felix felix 40096 Apr 23 13:27 setserial_2.17-46_i386.deb

/media/u10.04/pool/main/u:
total 12
drwx------ 2 felix felix 4096 Jul 16 11:17 ubiquity
drwx------ 2 felix felix 4096 Jul 16 11:17 ubiquity-slideshow-ubuntu
drwx------ 2 felix felix 4096 Jul 16 11:17 user-setup

/media/u10.04/pool/main/u/ubiquity:
total 240
-rw-r--r-- 1 felix felix  14538 Apr 23 13:27 oem-config_2.10.16_all.deb
-rw-r--r-- 1 felix felix 113120 Jul 18  2011 oem-config_2.2.27_all.deb
-rw-r--r-- 1 felix felix   4188 Apr 23 13:27 oem-config-gtk_2.10.16_all.deb
-rw-r--r-- 1 felix felix 105176 Jul 18  2011 oem-config-gtk_2.2.27_all.deb

/media/u10.04/pool/main/u/ubiquity-slideshow-ubuntu:
total 720
-rw-r--r-- 1 felix felix 734798 Apr 23 13:27 oem-config-slideshow-ubuntu_58_all.deb

/media/u10.04/pool/main/u/user-setup:
total 184
-rw-r--r-- 1 felix felix 187908 Apr 23 13:27 user-setup_1.42ubuntu3_all.deb

/media/u10.04/pool/main/w:
total 8
drwx------ 2 felix felix 4096 Jul 16 11:17 wvdial
drwx------ 2 felix felix 4096 Jul 16 11:17 wvstreams

/media/u10.04/pool/main/w/wvdial:
total 256
-rw-r--r-- 1 felix felix 174596 Jan 11  2010 wvdial_1.60.3_i386.deb
-rw-r--r-- 1 felix felix  85876 Apr 23 13:27 wvdial_1.61-4build1_i386.deb

/media/u10.04/pool/main/w/wvstreams:
total 1672
-rw-r--r-- 1 felix felix 183292 Jan  5  2010 libuniconf4.6_4.6.1-1_i386.deb
-rw-r--r-- 1 felix felix 125798 Apr 23 13:27 libuniconf4.6_4.6.1-2build1_i386.deb
-rw-r--r-- 1 felix felix 258602 Jan  5  2010 libwvstreams4.6-base_4.6.1-1_i386.deb
-rw-r--r-- 1 felix felix 201994 Apr 23 13:27 libwvstreams4.6-base_4.6.1-2build1_i386.deb
-rw-r--r-- 1 felix felix 490454 Jan  5  2010 libwvstreams4.6-extras_4.6.1-1_i386.deb
-rw-r--r-- 1 felix felix 441166 Apr 23 13:27 libwvstreams4.6-extras_4.6.1-2build1_i386.deb

/media/u10.04/pool/main/x:
total 4
drwx------ 2 felix felix 4096 Jul 16 10:34 xz-utils

/media/u10.04/pool/main/x/xz-utils:
total 224
-rw-r--r-- 1 felix felix 228052 Dec 22  2009 xz-utils_4.999.9beta+20091116-1_i386.deb

/media/u10.04/pool/restricted:
total 8
drwx------ 3 felix felix 4096 Jul 16 10:31 b
drwx------ 3 felix felix 4096 Jul 16 10:31 s

/media/u10.04/pool/restricted/b:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 bcmwl

/media/u10.04/pool/restricted/b/bcmwl:
total 2052
-rw-r--r-- 1 felix felix 1202502 Apr 23 13:27 bcmwl-kernel-source_5.100.82.38+bdcom-0ubuntu6_i386.deb
-rw-r--r-- 1 felix felix  894608 Apr 22  2010 bcmwl-kernel-source_5.60.48.36+bdcom-0ubuntu3_i386.deb

/media/u10.04/pool/restricted/s:
total 4
drwx------ 2 felix felix 4096 Jul 16 11:17 sl-modem

/media/u10.04/pool/restricted/s/sl-modem:
total 1012
-rw-r--r-- 1 felix felix 517564 Mar 23  2010 sl-modem-daemon_2.9.11~20100303-2_i386.deb
-rw-r--r-- 1 felix felix 512656 Apr 23 13:27 sl-modem-daemon_2.9.11~20110321-6_i386.deb

/media/u10.04/preseed:
total 12
-rw-r--r-- 1 felix felix 212 Apr 23 13:27 cli.seed
-rw-r--r-- 1 felix felix 497 Apr 23 13:27 ltsp.seed
-rw-r--r-- 1 felix felix 460 Apr 23 13:27 ubuntu.seed
felix@emma:~$ 
```

I emailed the supplier today about whether it was a solvable problem, though there's not a lot of consolation in being well paid doing up a parcel and then posting it.

-------------------

I was just about to send this when I decided to check something else. The flags ( BOOT in this case ) hadn't been transferred by dd, is this what you would expect? I was expecting the flag to be transferred. The working version had BOOT set on partition 1, but not the copy. When I manually set the boot flag it fixed the problem. Booted ok and files seem ok.

I'll mark as solved when I'm more sure it works.

I'm still surprised that your method worked, well, with a tiny bit of help, and yet the dd'ing the zeros didn't.

---

### Post by sudodus on 2012-07-16
> **F W Adams said:**
> I went and bought another flash USB today and set it up, it was fine.

I did as you suggested but rather as expected it didn't work. The transfer was of about 1GB from partition 1 of the ok system ( sdd1 ) to the bad one ( sdc1 ). SYNC took about 15 seconds so definately necessary. As expected it turned it into a 1GB device. I haven't looked in detail but the files seem fine, the disk label was transferred as well, it doesn't show as I changed the label of the ok one afterwards. Bad one: according to fdisk the format is FAT16, as it was before the transfer, but gparted has it as FAT16 before the transfer and F32 afterwrds. When booting there was just a blank screen.


fdisk, mount & two ls -l -R

```
felix@emma:~$ 
felix@emma:~$ sudo fdisk -l
...
Disk /dev/sdc: 3869 MB, 3869544448 bytes
105 heads, 18 sectors/track, 3998 cylinders, total 7557704 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009020b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048     7557119     3777536    6  FAT16

Disk /dev/sdd: 3999 MB, 3999268864 bytes
255 heads, 63 sectors/track, 486 cylinders, total 7811072 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *          63     2152709     1076323+   b  W95 FAT32
/dev/sdd2         2152710     7807589     2827440    b  W95 FAT32
...
```

I emailed the supplier today about whether it was a solvable problem, though there's not a lot of consolation in being well paid doing up a parcel and then posting it.

-------------------

I was just about to send this when I decided to check something else. The flags ( BOOT in this case ) hadn't been transferred by dd, is this what you would expect? I was expecting the flag to be transferred. The working version had BOOT set on partition 1, but not the copy. When I manually set the boot flag it fixed the problem. Booted ok and files seem ok.

I'll mark as solved when I'm more sure it works.

I'm still surprised that your method worked, well, with a tiny bit of help, and yet the dd'ing the zeros didn't.

The target pen-drive is smaller than the source one

Disk /dev/sdc: 3869 MB
Disk /dev/sdd: 3999 MB

also heads, sectors/track and cylinders differ.

When the target is smaller the dd cloning is truncated. This might cause problems. Also it is strange that the heads, sectors/track and cylinders differ. 255 heads, 63 sectors/track are standard values for modern drives. Maybe it would help if you change those values. See ```
man fdisk
```

A successful cloning would certainly copy also the boot flag. I'm glad you observed that difference and could fix it :KS

Anyway, those four pendrives really behave in a strange way.

---

### Post by F W Adams on 2012-07-17
> The target pen-drive is smaller than the source one

Disk /dev/sdc: 3869 MB
Disk /dev/sdd: 3999 MB


No arguing with 3999 > 3869 but the dd was only asked to copy the first partition, and about 1000 < 3869. When source is really bigger than destination it gives an error message.

-------

Is it possible the KINGSTON drive is storing the partition flags in the area before the partitions start and consequently not looking at them on copy paritions?

Anyway glad to have it fixed. Thanks.

---

### Post by sudodus on 2012-07-17
> **F W Adams said:**
> No arguing with 3999 > 3869 but the dd was only asked to copy the first partition, and about 1000 < 3869. When source is really bigger than destination it gives an error message.

I see. Yes, that first partition should have been copied correctly. Provided that the settings for heads, sectors/track and cylinders won't create problems.
> 
Is it possible the KINGSTON drive is storing the partition flags in the area before the partitions start and consequently not looking at them on copy paritions?

Anyway glad to have it fixed. Thanks.

I'm not sure, but probably the partition table including flags is located in the MBR (the head of the drive, before the partitions), and I think this is also where the settings for heads, sectors/track and cylinder reside. So if you copy also the first 512 bytes from the good drive to the bad one, you might repair everything.

---

### Post by ame82 on 2012-10-02
> **Cheesehead said:**
> Double-check that you used a valid 10.04 image.
Try making the USB Stick again.

The directory listing you posted seems to have neither a kernel or a compressed-system to use that kernel, both of which come from the 10.04 image.

what if i am using ubuntu 12.04 
i am tryiing to make HBCD using the iso file and unetbootin but it boot only to main screen where is the only choise is default and when i click it it doesnt do anything and my hbcd doesnt start

---

