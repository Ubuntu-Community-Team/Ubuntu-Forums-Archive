---
title: "/etc/fstab is gone!!!! Help needed!"
date: 2006-03-26
forum: General Help
---

### Post by Adanufgail on 2006-03-26
When I booted, I got an error when it tried to boot /dev/hdb2 to /root. Upon issuing the command "more /etc/fstab" I got a file not found error. I cd'd to the directory and typed "ls" and there was **NO** fstab! What can I do?

---

### Post by Xian on 2006-03-26
You should have a backup at /etc/fstab~ if you've ever modified that file.

---

### Post by Adanufgail on 2006-03-26
contents of /etc/fstab:
udev/
modprobe.d

---

### Post by Xian on 2006-03-26
Well, if you don't have a backup you'll have to create a new one.
An easy way would be to boot the LiveCD and copy over its fstab.

---

### Post by aysiu on 2006-03-26
[QUOTE=Xian]Well, if you don't have a backup you'll have to create a new one.
An easy way would be to boot the LiveCD and copy over its fstab.[/QUOTE] I'm not sure if that'll work, since the live CD creates its own fake partitions in RAM.

This probably won't help, but this is my /etc/fstab: ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
``` If you know where your / partition is, you can change it from /dev/hda7 to whatever it is...

---

### Post by Adanufgail on 2006-03-26
huh, how would I get that into Ubuntu?
I don't suppose I could just type it in Notepad and save it to a disk...

---

### Post by aysiu on 2006-03-26
[QUOTE=Adanufgail]huh, how would I get that into Ubuntu?
I don't suppose I could just type it in Notepad and save it to a disk...[/QUOTE] You would have to boot with a live CD, mount your Ubuntu partition and then create a new fstab file in the /etc folder.

---

### Post by Adanufgail on 2006-03-26
when I try to mount it, I get:
> wrong fs type, bad option, bad superblock on /dev/hdb2, or too many mounted file systems

---

### Post by Adanufgail on 2006-03-26
I'm starting to think the whole fs might be corrupted...should I reformat or is there hope?

---

### Post by Toxicity999 on 2006-03-26
If you have the space and time and want the easiest possiple solution (not much thought to it.) install ubuntu to some extra space, doesnt need to be huge just enough to fit it all temporarily, swipe the fstab that creates and slide it into your original partition (should have been mounted itself. Note: Might want to remove any extra references. Of course, make sure it's in a format like this (similar to anyway):

proc            /proc           proc    defaults        		              0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 	0       1
/dev/hdc1       none        swap    sw              		                   0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto            0       0

---

### Post by aysiu on 2006-03-26
[QUOTE=Adanufgail]I'm starting to think the whole fs might be corrupted...should I reformat or is there hope?[/QUOTE] Well, when you're booted to the live CD, can you post the output here of these commands? ```
sudo fdisk -l
df -h
``` Also, do you know if your Ubuntu partition is Ext3 or Reiserfs?

---

### Post by Adanufgail on 2006-03-27
# sudo fdisk -l:

Disk /dev/sda: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          10       80293+   0  Empty
/dev/sda2   *          11        3648    29222235    b  W95 FAT32

Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14593   117218241    c  W95 FAT32 (LBA)

Disk /dev/hdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1       26757   214925571    7  HPFS/NTFS
/dev/hdb2           26758       38307    92775375   83  Linux
/dev/hdb3           38308       38913     4867695   82  Linux swap

---------------------------------------------------------
df -h:

Filesystem            Size  Used Avail Use% Mounted on
/dev/root             2.5M  1.7M  756K  70% /
/dev/cdrom            700M  700M     0 100% /cdrom
/dev/cloop            1.9G  1.9G     0 100% /KNOPPIX
/ramdisk              398M  2.7M  395M   1% /ramdisk

I used a KNOPPIX boot disk rather than download a UBUNTU one...Is that a problem? I can download it if it is... Oh, and my Ubuntu partition (hdb2) is ext3.

---

### Post by aysiu on 2006-03-27
Okay. You're in Knoppix. Go ahead and click on the /dev/hdb2 icon on the desktop--that should mount Ubuntu.

You need to open it as root, though, not as user, so find the File Manager - Super User Mode button in the KMenu and navigate to /mnt/hdb2 or whatever the appropriate directory is.

Create a text file called *fstab* in the /etc folder and paste in ```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
``` Then save and reboot... and cross your fingers!

---

