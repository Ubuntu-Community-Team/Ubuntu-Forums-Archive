---
title: "Other Disk Partitions Not Recognized?"
date: 2006-03-18
forum: General Help
---

### Post by teodortenchev on 2006-03-18
I don't know how to view the files on my other disk partitions. I installed Ubuntu on a separate partition and I have my games on another one (using the NTFS file system). My question is how to make it so that I can use this partition as well? On Knoppix (Live CD) there was an option to mount the partitions and it was directly on the desktop. I can't find anything like this with this OS.


When I go to filesystem all I see is the partition with the OS and no other partitions.

---

### Post by Zelut on 2006-03-18
Other partitions aren't mounted by default but its pretty easy to do.  I, for example, have my XP partition mounted at boot so I can browse my documents & music (or whatever).

If you could post the output of 'sudo fdisk -l' I'm sure we can tell you how you can very simply add your other disk partitions at boot.

---

### Post by Ramses de Norre on 2006-03-18
Make a mountpoint for each partition (sudo mkdir /media/hda1 for example, partitions mounted in /media show automatically at Desktop).
Then add a line for each partition in /etc/fstab (sudo gedit /etc/fstab) similar to this one: ```
/dev/hda2       /media/windowsc  ntfs    nls=utf8,umask=0222 0       0

```
change the partition numbers and mountpoints to yours.

---

### Post by aysiu on 2006-03-18
Ramses' instructions are good.

You can also see:
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

or:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by teodortenchev on 2006-03-18
Sorry but I'm a complete noob. Where do I enter those commands? (do I need to open a terminal or something?)

---

### Post by teodortenchev on 2006-03-18
This is what I get with the first command.


sudo fdisk -l

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
teodor@catv-home-user-00100:~$ sudo fdisk -I
fdisk: invalid option -- I

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors

---

### Post by teodortenchev on 2006-03-18
sudo fdisk -l

Disk /dev/hda: 82.3 GB, 82348277760 bytes
255 heads, 63 sectors/track, 10011 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1086     8723263+   7  HPFS/NTFS
/dev/hda2            1087       10010    71682030    f  W95 Ext'd (LBA)
/dev/hda5            1087        5451    35061831    7  HPFS/NTFS
/dev/hda6            6186       10010    30724281    7  HPFS/NTFS
/dev/hda7   *        5452        6150     5614686   83  Linux
/dev/hda8            6151        6185      281106   82  Linux swap / Solaris

Partition table entries are not in disk order
teodor@catv-home-user-00100:~$
teodor@catv-home-user-00100:~$

---

### Post by aysiu on 2006-03-18
It looks as if you have three NTFS partitions. I'm not sure which one you want mounted or if you want them all mounted.

Can you do one more thing? Post the output of this command as well? ```
cat /etc/fstab
```

---

### Post by teodortenchev on 2006-03-19
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda8       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0



I want to mount all drives.

---

### Post by Ramses de Norre on 2006-03-19
In terminal do sudo mkdir /media/name 
Set the name you want them do be displayed with instead of name.
Then do sudo gedit /etc/fstab and add a line similar to the one I gave for each partition.
Where it says /media/windowsc in mine, you should change the windowsc in the name you defined earlier and change hda2 in the code for the partition you want to mount there (look for the codes with sudo fdisk -l).
Do this for every partition you want to mount.

---

### Post by teodortenchev on 2006-03-19
I found an easier way to mount them. System --->Administration-->Disks :)

---

### Post by xmastree on 2006-03-19
[QUOTE=teodortenchev]Sorry but I'm a complete noob. Where do I enter those commands? (do I need to open a terminal or something?)[/QUOTE]

Ok, looking at your fdisk -l results, I'll assume that you want to mount the three ntfs partitions, which are hda1,5&6.

First you need to create three mouint points. You can call them anything, and put them anywhere but the usual place is in /mnt so, let's make them /mnt/hda1 /mnt/hda5 and /mnt/hda6

First, open a terminal and type these three commands:
```
sudo mkdir /mnt/hda1
sudo mkdir /mnt/hda5
sudo mkdir /mnt/hda6
```That's the mount points created, next you need to modify your fstab to include them, so open it with gedit```
sudo gedit /etc/fstab
```
and add these three lines to the end of it:

```
/dev/hda1	/mnt/hda1	ntfs	umask=0222	0	0
/dev/hda5	/mnt/hda5	ntfs	umask=0222	0	0
/dev/hda6	/mnt/hda6	ntfs	umask=0222	0	0
```
Save the file and exit the editor.

Next, mount them as per the table by doing this:
```
sudo mount -a
```

Then, assuming there are no errors, you can see if they're mounted by typing ```
mount
```which will list what is mounted and where.

Since they're ntfs, you won't be able to write to them, only read. If you want a shared partition, better to convert one of them to fat32. If you do that, the entry in fstab will need to be changed from **ntfs** to **vfat**, and the umask should change from **0222** to **000**

---

### Post by teodortenchev on 2006-03-19
I get an error when trying to access any folder. "Cannot launch entry"


I cant even launch the terminal.

---

### Post by teodortenchev on 2006-03-19
Ok, here is what I get after all of this:

/dev/hda7 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
/dev/hda1 on /mnt/hda1 type ntfs (rw,umask=0222)
/dev/hda5 on /mnt/hda5 type ntfs (rw,umask=0222)
/dev/hda6 on /mnt/hda6 type ntfs (rw,umask=0222)



Is that OK?


How do I access them now?

---

### Post by Ramses de Norre on 2006-03-19
Looks ok to me.
There under the mountpoint, so the first is accessed by browsing to /mnt/hda1.
But if you mount them under /media as I adviced they will be on your Desktop automatically. (You can of course create a symlink to the mount point also.)

---

### Post by teodortenchev on 2006-03-19
:'(

There is nothing on my desktop plus I can't move anything to the trash from anywhere (even on the Unbutu partition). It says I don't have sufficient permissions.


I can access them by clicking browse on the Disks setup in the admin panel.

---

### Post by Ramses de Norre on 2006-03-19
As I said you need to mount them under /media or make a symlink yourself to get them on your desktop.
Maybe creating a symlink is the easiest way: ```
ln -s /mnt/hda1 ~/Desktop/hda1
```
Do so for all the partitions.
What are the permissions on ~/.Thrash? Do ls -la in your home folder and copy the line ending with .Trash to here.

---

### Post by teodortenchev on 2006-03-19
Did that and every shortcut leads to the same partition.

(I did change the numbers when adding the rest of the partitions)

---

### Post by Ramses de Norre on 2006-03-19
You have changed the partition number in the name AND the mountpoint in the ln commands?
If so: check your fstab for mistakes, maybe you typed something wrong in there.

---

### Post by aysiu on 2006-03-19
[QUOTE=Ramses de Norre]You have changed the partition number in the name AND the mountpoint in the ln commands?
If so: check your fstab for mistakes, maybe you typed something wrong in there.[/QUOTE] Actually, just post your revised /etc/fstab here, and we'll tell you if there are mistakes.

---

