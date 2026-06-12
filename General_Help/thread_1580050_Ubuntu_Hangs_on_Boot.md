---
title: "Ubuntu Hangs on Boot"
date: 2010-09-22
forum: General Help
---

### Post by Nathaniel D. on 2010-09-22
A few weeks ago, I installed Ubuntu 10.04 from a flash drive as a dual boot with Windows XP on an NB205 laptop. The installation went fine, but whenever I tried to reboot (not sure if it started at or after the first reboot), it would give me this message after the boot menu:

```
 Gave up waiting for root device. Common problems:
    - Boot args (cat /proc/cmdline)
     - Check rootdelay = (did the system wait long enough?)
     - Check root = (did the system wait for the right device?)
    - Missing modules (cat /proc/modules: ls /dev)
 ALERT! /dev/disk/by-uuid/0244b6 b-ab4f-4058-b4c1-2e6c3942f954 does
 not exist. Dropping a shell!
BusyBox v1.13.3 (Ubuntu 1:1.13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.
(initramfs)_

```

Where that last underscore represents a blinking cursor line. Pressing enter would produce another instance of '(initramfs)_' on the next line. Entering 'help' would display a list of commands (which I didn't write down). Entering 'exit' would move the cursor line to a new line, and after that the system would eventually load.
Some days after that, it stopped displaying that message, and became simply a black screen with only the blinking line. It still boots (as it always has), but takes 5-10 minutes. During the first *and* last 20 seconds or so, I can type, but between that, I find only the alt+[F keys] produce any visible changes.
And just to clarify, besides the boot time, Ubuntu runs perfectly.

**Things I have Tried**
(while the message appeared during boot)
1. [http://ubuntuforums.org/showpost.php?p=6581939&postcount=322](http://ubuntuforums.org/showpost.php?p=6581939&postcount=322) (however, when I opened /boot/grub/menu.lst as per the second part of the instructions, it was blank, so I didn't continue)

(after the message stopped appearing during boot)
2. Holding down 'Shift'. This created:
```
[  0.763984]VFS: Cannot open root device "sda5" or unknown-block(0,0)
[  0.764065] Please append a correct "root=" boot option; here are the available partitions:
      [   0.759689] Kernel panic &#8211; not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```
I was able to fix this by booting into the flash drive and doing what AgenT said in [http://ubuntuforums.org/showthread.php?t=296809&highlight=kernel+panic](http://ubuntuforums.org/showthread.php?t=296809&highlight=kernel+panic)

3. Removing the Floppy Disk Drive (which I don't have)
I have Phoenix TrustedCore BIOS, so I couldn't find the floppy, and evidently it was never installed.

4. Updating my kernel by [http://www.gidforums.com/t-1990.html](http://www.gidforums.com/t-1990.html)
I stopped at step 3, as it couldn't find /usr/src/linux.config

5. Updating my kernel by [http://ubuntuforums.org/showthread.php?t=43065](http://ubuntuforums.org/showthread.php?t=43065)
The first terminal code (sudo apt-get install linux-tree) produced:
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: couldn't find package linux-tree
```
The other codes produced login and other errors, which I fixed with [http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories](http://ubuntuguide.org/wiki/Ubuntu_dapper#Repositories); however, the first code still gives an error.

6. Booting into Recovery Mode
Same boot time, though perhaps a tad faster.

7. Pounding on the keyboard.
Specifically Alt+[F keys], followed by 'exit' and 'continue'. This actually worked, in a sense, by decreasing the boot time to about a minute. However, I don't wish to do this every time.

8. Running 'sudo update-grub'
No change.

**Various Other Glitches Which May Have Some Bearing**
1. The sound didn't work (solved by [http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04](http://monespaceperso.org/blog-en/2010/05/02/upgrade-alsa-1-0-23-on-ubuntu-lucid-lynx-10-04)). This has happened three times, and was fixed twice (yeah, I have no sound right now).
2. At login, my password wasn't accepted (solved by suspending). This happened twice.
3. At login, the 'u' key would move the cursor back a space, instead of inputting 'u' (solved by suspending). This happened once.
4. Clicking anywhere would only minimize and maximize an open window (solved by suspending). This happened at least twice.
5. Cursor wouldn't move, but after about 10 minutes, would (solved by suspending). This happened at least twice.
6. Windows XP doesn't load. It reaches the snail-crawling loading screen, then reboots. I gave the Ubuntu partition a bit more room during installation; don't know if that has anything to do with it.

I've been trying to fix this ever since I installed Ubuntu, so I'd really appreciate it if I could get this fixed. Thanks in advance.

---

### Post by andrewthomas on 2010-09-23
post the output of 

```
sudo blkid
sudo fdisk -lu
cat /etc/fstab
```[FONT=monospace]
[/FONT]

---

### Post by Nathaniel D. on 2010-09-23
> **andrewthomas said:**
> post the output of 

```
sudo blkid
sudo fdisk -lu
cat /etc/fstab
```[FONT=monospace]
[/FONT]

sudo blkid:
```
/dev/sda1: LABEL="TI100277P0G" UUID="54D0DC47D0DC30CA" TYPE="ntfs" 
/dev/sda2: LABEL="HDDRECOVERY" UUID="0401-0163" TYPE="vfat" 
/dev/sda5: UUID="0244b63b-ab4f-4058-b4c1-2e6c3942f954" TYPE="ext4" 
/dev/sda6: UUID="5f1e70d7-f842-46cd-b4ad-a50349dca4f2" TYPE="swap"
```

sudo fdisk -lu
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9e779e77

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63   187546048    93772993    7  HPFS/NTFS
/dev/sda2       296849070   312576704     7863817+  1c  Hidden W95 FAT32 (LBA)
/dev/sda3       187547646   296847359    54649857    5  Extended
/dev/sda5       187547648   292290559    52371456   83  Linux
/dev/sda6       292292608   296847359     2277376   82  Linux swap / Solaris

Partition table entries are not in disk order
```

cat /etc/fstab:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0244b63b-ab4f-4058-b4c1-2e6c3942f954 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=5f1e70d7-f842-46cd-b4ad-a50349dca4f2 none            swap    sw              0       0
```

---

### Post by andrewthomas on 2010-09-24
I would do this: 

[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

