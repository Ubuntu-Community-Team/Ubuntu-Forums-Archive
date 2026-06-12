---
title: "Formatting USB Drives"
date: 2006-06-21
forum: General Help
---

### Post by MechaGanon on 2006-06-21
Is there a terminal code to re-format my USB drive? :confused:

---

### Post by kzutter on 2006-06-21
mkfs is the basic command but you will have to supply it information, at least the filesytem type and the device name.
Type 'man mkfs' at the command line for more info about this command.

You did not mention if this is a block device or flash drive - it will prbably make a difference.

---

### Post by MechaGanon on 2006-06-21
Well I don't know... I'm pretty sure it's a flash drive.

That man mfks thing confused me. IS there at least a way to like delete this stuff off? It's 256 mb and it says that there's like 40 gb stuff on it... and it locked itself up so I can't delete it without going through terminal or something.

I'd get help from my brother but he's gone...

---

### Post by aysiu on 2006-06-21
Do you have to use the terminal to format it? What's wrong with this? ```
sudo aptitude update
sudo aptitude install gparted gksu
gksudo gparted
``` GParted should let you format it (you'll have to unmount it first, which you can also do in GParted).

---

### Post by MechaGanon on 2006-06-21
Thank you! I just thought that terminal would be easiest...

Came up with

> Error While deleting
"/media/usb...icious.mp3" cannot be deleted because it is on a read-only disk.

Nevermind. It worked.

---

### Post by c0d4041292 on 2006-07-17
hi, i have a 512mb usb flash device and i can put stuff on it copy stuff from it but i can not delete anything off of it. can someone help me.

---

### Post by aysiu on 2006-07-17
> **c0d4041292 said:**
> hi, i have a 512mb usb flash device and i can put stuff on it copy stuff from it but i can not delete anything off of it. can someone help me.
Can you plug the drive in and then post back here (copy and paste the text) the output of these commands? ```
sudo fdisk -l
df -h
cat /etc/fstab
```

---

### Post by c0d4041292 on 2006-07-17
by the way....im a noob



cody@blackboy:~$ sudo fdisk -l
Password:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14216   114189988+  83  Linux
/dev/sda2           14217       14593     3028252+   5  Extended
/dev/sda5           14217       14593     3028221   82  Linux swap / Solaris

Disk /dev/sdb: 515 MB, 515899392 bytes
16 heads, 32 sectors/track, 1968 cylinders
Units = cylinders of 512 * 512 = 262144 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1968      503792    6  FAT16
cody@blackboy:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             108G  5.0G   97G   5% /
varrun                506M   80K  506M   1% /var/run
varlock               506M  4.0K  506M   1% /var/lock
udev                  506M  140K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
lrm                   506M   19M  488M   4% /lib/modules/2.6.15-26-386/volatile
/dev/sdb1             492M  433M   60M  88% /media/UDISK 20X
cody@blackboy:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hde        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by aysiu on 2006-07-17
I see your drive is /dev/sdb1 and is getting automounted to /media/UDISK. Ordinarily, this would be fine, but apparently things don't seem to be working for you. Try copying and pasting these commands: ```
sudo umount /dev/sdb1
sudo mkdir /udisk
sudo cp /etc/fstab /etc/fstab_backup
sudo nano /etc/fstab
``` Then paste this line at the end of that file ```
/dev/sdb1 /udisk vfat iocharset=utf8,umask=000 0 0
``` and save (Control-X, Y, Enter) and finally ```
sudo mount -a
``` Then go to the /udisk directory and see if you have the same problem.

---

