---
title: "Win7 (from grub) deliveres only flashing cursor"
date: 2012-01-03
forum: General Help
---

### Post by jamesisin on 2012-01-03
I have a machine with Ubu 10.04, WinXP, and Win7 partitions.  The Win7 partition was the last built and it broke grub.  I have fixed grub and I can select anything from the grub menu (except 7) and it acts as expected.

When I try to boot 7 I just get a flashing cursor and nothing more.

What do I need to do to grub (or the Win7 files/partitions) to get that partition to boot properly?

(You can see more information [here]("http://ubuntuforums.org/showthread.php?t=1890926").)

---

### Post by Anstice on 2012-01-03
Do you need both XP and 7? I only ask because I ran into this problem and unfortunately could only remedy it by removing XP.

Could you post the result of ```
fdisk -l
``` so we can your partition layout?

---

### Post by jamesisin on 2012-01-03
Here you are:

```
sudo fdisk -l
[sudo] password: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa541a541

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3191    25631676    7  HPFS/NTFS
/dev/sda2            3192        3204      104422+   7  HPFS/NTFS
/dev/sda3            8983       19458    84142081    5  Extended
/dev/sda4            3205        8982    46411785    7  HPFS/NTFS
/dev/sda5            8983       19084    81136640   83  Linux
/dev/sda6           19084       19458     3004416   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x9d74f599

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2              13        5485    43954838+   7  HPFS/NTFS
```

(You can ignore sdb as I will be removing that drive shortly.)

---

### Post by Anstice on 2012-01-03
That's much the same as my old setup. Do you have access to a Windows 7 install disk? I found that the restore/repair feature on that works most of the time.

Another thing I sometimes found worked was to open GParted and check which partition the boot flag was set on.

Also, what is the function of your /dev/sda1 partition?

---

### Post by jamesisin on 2012-01-03
Here is a breakdown of all the partitions and their usages:

sda1 XP
sda2 System Reserved [contains a bunch of boot information; relates to Win7]
sda3 extended (Ubu)
sda4 Win7
sda5 Ubu
sda6 swap

(3 contains 5 & 6.)

The only partition GParted shows as boot flagged (and you can see this in fdisk above) is sda1.

---

### Post by jamesisin on 2012-01-03
I notice that when I update grub it uses that System Reserved partition for 7:

```
$ sudo update-grub
[sudo] password: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-37-generic
Found initrd image: /boot/initrd.img-2.6.32-37-generic
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Microsoft Windows XP Professional on /dev/sda1
Found Windows 7 (loader) on /dev/sda2
done
```

---

### Post by oldfred on 2012-01-03
Windows only boots from the active partition which we see as the one with the boot flag. Grub does not use boot flag. Windows jumps to the PBR - partition boot record/sector to continue to boot. Any additional installs of Windows litterally put all the boot files in the active partition. Some delete the active partition as the second install is newer and wonder why they cannot boot Windows at all.

If you boot your sda1, it should give you the choice to boot either Windows.

To get each MS to have its own boot loader make a primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by jamesisin on 2012-01-03
Using sda1 boots directly into XP.  I suspect the person who loaded 7 knew nothing about multi-booting as they left the system with only Win7 booting.  Rather broke everything I'd done with XP and Ubu.  I've fixed it except for getting 7 to actually boot.  Just that damned flashing pre-OS cursor (ctrl-alt-del reboots so you know Win has not take over at all).

I have tried moving and also removing the boot flag (all three NTFS partitions and now no boot flag), and this has changed nothing.

I suppose I could do a repair on 7 and then fix grub again, but since I have access to all the boot files on the NTFS partition I ought to be able to make any changes necessary without doing so.

---

### Post by oldfred on 2012-01-04
Windows repairs the partition with the boot flag (active partition). You might be able to move boot files to Windows 7, move boot flag to Windows 7 partition and run the repairs. If XP does not work, move boot flag back to XP partition and repair it.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Grub does not use boot flag, but if Windows boot files are in a NTFS primary partition, grub2's os-prober will add a boot stanza to the grub menu. Whether it works or not will be if Windows would boot on its own with the boot flag on that partition and a Windows boot loader in the MBR. If you run auto repairs (needs 3 times) it will put the Windows boot loader in the MBR, so you have to be prepared to reinstall grub2's boot loader.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2")

---

### Post by jamesisin on 2012-01-16
In the end I had to reinstall the Windows 7 partition(s) (oh, how I tried not to) and then I used boot-repair (from a 10.04 live CD) to make everything right.  Now Grub controls all of the OS partitions which all boot as expected.

---

### Post by jamesisin on 2012-02-03
My blog post concerning how I fixed this:

[http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/](http://jamesisin.com/a_high-tech_blech/index.php/2012/01/repairing-grub-after-windows-breaks-it/)

---

