---
title: "Grub Problems. Boot Hangs at &quot;Verifiying DMI Data pool&quot;"
date: 2009-08-25
forum: General Help
---

### Post by charliehorse55 on 2009-08-25
I just bought a OCZ Vertex SSD. I used to have Ubuntu installed on a 1 TB Caviar black drive, however I now want to configure it so that 

"/" is mounted on the SSD
and 

"/home/" is mounted to the 1 TB caviar black. 

I edited the fstab file:

```
# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=6dc298d9-d391-48fd-b34d-3119b8645d24 /home           ext3    relatime,erro$
# swap was on /dev/sda5 during installation
UUID=b0352158-c39f-4097-af5b-d1887eeb0bf7 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

/dev/sdb1      /      ext4   0    0

```

Then I booted from the live cd and copied the contents of "/" from the 1 TB to the SSD, omiting the home folder and leaving it on the drive. 

I then did this: 

```
sudo fdisk -l

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0001d94c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      120145   965064681   83  Linux
/dev/sda2          120146      121601    11695320    5  Extended
/dev/sda5          120146      121601    11695288+  82  Linux swap / Solaris

Disk /dev/sdb: 32.0 GB, 32017047552 bytes
32 heads, 32 sectors/track, 61067 cylinders
Units = cylinders of 1024 * 512 = 524288 bytes
Disk identifier: 0x261d0686

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       61067    31266288   83  Linux

Disk /dev/sdc: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0002a044

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       12754   102446473+   7  HPFS/NTFS
/dev/sdc2           12755       14593    14771767+  83  Linux
ubuntu@ubuntu:~$ sudo grub
Probing devices to guess BIOS drives. This may take a long time.

       [ Minimal BASH-like line editing is supported.   For
         the   first   word,  TAB  lists  possible  command
         completions.  Anywhere else TAB lists the possible
         completions of a device/filename. ]
grub> find /boot/grub/stage1 
find /boot/grub/stage1
 (hd0,0)
 (hd1,0)
 (hd2,1)
grub> root (hd1,0)
root (hd1,0)
grub> setup (hd1,0)
setup (hd1,0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd1,0)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd1,0) /boot/grub/stage2 p /boot/grub/menu.lst "... succeeded
Done.
grub> quit
quit
ubuntu@ubuntu:~$ 

```

After doing that, I rebooted and selected the SSD as the booting drive in the bios. I boot up, and it hangs at "Verifying DMI Data Pool"

I'm at a loss as to what happened. I installed grub, but on boot grub never appears. 

What's going on?

---

### Post by dandnsmith on 2009-08-25
The 'verifying DMI Data Pool' is produced by the BIOS before you get into any boot sequence at all - nothing to do with GRUB.
You'll have to look at the hardware changes you made to find the cause (something like your new drives), and resolve the problem.

[This posting](http://www.duxcw.com/faq/computer/dmi.html) is one I found by googling, and [this](http://www.computerhope.com/issues/ch000474.htm) is another - there are lots more!!

---

