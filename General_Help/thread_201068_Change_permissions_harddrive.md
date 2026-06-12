---
title: "Change permissions harddrive"
date: 2006-06-21
forum: General Help
---

### Post by freddy50 on 2006-06-21
what I did before:
mount all my hard drives under ubuntu,
-change the fstab
with ```
gedit /etc/fstab 

proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/sda5       /media/sda5     ntfs    defaults,umask=0000        0       0
/dev/hda5       /media/hda5     ntfs    defaults,umask=0000        0       0
/dev/hda1       /media/hda1     ntfs    defaults,umask=0000        0       0
```
I added all the drives.
Then under Root I mounted all the drives.
but now when I want to change any file on a drive, it says permission denied.

what I tried:
```
sudo nautilus
```, but there doesn't seem to be an option to change the permissions.

can someone please help? :rolleyes:

---

### Post by kb3hkg on 2006-06-21
Which permissions are you trying to change? Linux support for ntfs is still interesting to say the least.

---

### Post by freddy50 on 2006-06-21
I want write access :D . I already have read & execute

---

### Post by kb3hkg on 2006-06-21
on ntfs good luck, I have yet to hear of it working bug free for writing.

---

### Post by Ramses de Norre on 2006-06-21
There is still no safe way to write on ntfs from Linux.. It's being developped but many bugs remain untill now.. So it's possible but very dangerous.

---

### Post by kb3hkg on 2006-06-21
What are you using these drives for? If it is essential for you to be able to write to them you may want to consider a different file system if possible.

---

### Post by Jasper Houtman on 2006-06-21
If you wan't a shared drive just convert one to fat32. worked like a charm for me.

---

### Post by eth on 2006-06-21
Jasper's Option it's the best choice, of course, if you just can't let winblows go, at least have a vfat (FAT32) partition, so you'll have r-w-x perissions from both OS.

Writing on NTFS it's up till now *strongly discouraged* 

Do as you will, but don't come complaining you can't boot winpawns anymore! ;) 
Joking, really now, if you've got a completely free and harmless ntfs partition, make your writing experiment, and post the results...but...it's not supported!

---

### Post by sabredog on 2006-06-22
I have a similar issue with my FAT32 drive and my external drive. How can I change permissions to match the permission set of my home folder, thus allowing me full reign over the contents of the drives?

Here is the contents of my fstab file showing my drive set-up. The external drive is partitioned into two FAT32 partitions of roughly 20Gb each and Dapper has automounted those once detected via USB.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1    /media/windows        ntfs    nls=utf8,umask=0222    0    0
/dev/hdc1    /media/documents    vfat    umask=000    0    0
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

```

EDIT: Funnily enough, my XP Network shares give me full permissions as well.

Is it the mount point locations, should they be located in the home folder or is it a switch/param issue?

Can anyone help?

---

### Post by kb3hkg on 2006-06-22
The problem is that fat32 doesn't support permissions

---

### Post by Ramses de Norre on 2006-06-22
For full permissions add an option umask=0000

---

### Post by sabredog on 2006-06-22
Part or perhaps all of the problem is that the external and the internal FAT32 dirves are owned by root and not by the user. Would that have a bearing on this?

If so can it be changed?

---

### Post by aysiu on 2006-06-22
That will never change. The best you can do for FAT32 is have it be "owned" by root and with read/write permissions for everyone and for NTFS to be "owned" by root and with read permissions for everyone.

Neither FAT32 nor NTFS really supports Linux permissions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by mlind on 2006-06-22
You could use umask=007 and gid=6 (disk) as mount options and add users which
can read/write/execute to disk group.

This way root and disk would have all permissions, and others none.

---

### Post by sabredog on 2006-06-22
[QUOTE=aysiu]That will never change. The best you can do for FAT32 is have it be "owned" by root and with read/write permissions for everyone and for NTFS to be "owned" by root and with read permissions for everyone.

Neither FAT32 nor NTFS really supports Linux permissions.

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)[/QUOTE]

I am happy for that to be the case but why cannot such software packages as Azureus create a file on a FAT32 drive?

This has got me puzzled.

BTW, your guides are superb. I used them when I first installed Ubuntu Linux

---

### Post by aysiu on 2006-06-23
No idea.

I have to say it's not the first I've heard of it--weird situations with FAT32 where you can put files on there but your file sharing program can't. It may have to do with FAT32 not supporting Linux permissions. I'm not sure.

You wouldn't happen to have mounted that FAT32 partition within the /media or /mnt folders, would you have? Sometimes that can screw up permissions in a weird way. I prefer to mount to a static, fake directory like /fat_drive or /azureus.

---

### Post by sabredog on 2006-06-23
[QUOTE=aysiu]No idea.

I have to say it's not the first I've heard of it--weird situations with FAT32 where you can put files on there but your file sharing program can't. It may have to do with FAT32 not supporting Linux permissions. I'm not sure.

You wouldn't happen to have mounted that FAT32 partition within the /media or /mnt folders, would you have? Sometimes that can screw up permissions in a weird way. I prefer to mount to a static, fake directory like /fat_drive or /azureus.[/QUOTE]

Certainly did as I wanted the drive icon to appear on my desktop. here is a list of my fstab file.

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1    /media/windows        ntfs    nls=utf8,umask=0222    0    0
/dev/hdc1    /media/documents    vfat    umask=000    0    0
/dev/hdc5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0

```

So if that might be the issue, can I move the folder and still get the drive icon to appear on the desktop?

How can that be done - by editing the fstab pointing to a new location after copying the contents of the old folder to the new one?

---

### Post by aysiu on 2006-06-23
I don't know if this will solve your problem, but it's worth a shot, I think. ```
sudo mkdir /documents
sudo umount /dev/hdc1
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
``` Replace your current line with this one: ```
/dev/hdc1    /documents    vfat    umask=000    0    0
``` Save and exit. ```
sudo mount -a
ln -s /documents ~/Desktop/documents
``` That should work. Let me know. If it doesn't, and you want it back the way it was, I can walk you through that as well.

---

### Post by sabredog on 2006-06-23
[QUOTE=aysiu]I don't know if this will solve your problem, but it's worth a shot, I think. ```
sudo mkdir /documents
sudo umount /dev/hdc1
sudo cp /etc/fstab /etc/fstab.backup
gksudo gedit /etc/fstab
``` Replace your current line with this one: ```
/dev/hdc1    /documents    vfat    umask=000    0    0
``` Save and exit. ```
sudo mount -a
ln -s /documents ~/Desktop/documents
``` That should work. Let me know. If it doesn't, and you want it back the way it was, I can walk you through that as well.[/QUOTE]

Certainly worked BUT the same savefile error occurs. Perhaps I need to run Azureus for example via SUDO. I do not want to do that though.

How do I remove the /documents folder link from the desktop, sitting next to the drive icon? If I try to delete it, I get a warning message "Not on the same file system"

---

### Post by aysiu on 2006-06-23
Darn. I'm not sure what to do about that. Yeah, running Azureus as *sudo* would be a bad idea.

```
sudo rm ~/Desktop/documents
``` doesn't work?

---

### Post by sabredog on 2006-06-23
[QUOTE=aysiu]Darn. I'm not sure what to do about that. Yeah, running Azureus as *sudo* would be a bad idea.

```
sudo rm ~/Desktop/documents
``` doesn't work?[/QUOTE]

That did it!

BTW, how do I reverse the process I just undertook?

I will have to live with this. Funny as Bittornado will cheerfully create a file on the same drive Azureus cannot???

---

### Post by aysiu on 2006-06-23
Reversing the steps: ```
sudo umount /dev/hdc1
sudo rmdir /documents
sudo cp /etc/fstab.backup /etc/fstab
sudo mount -a
```

---

### Post by sabredog on 2006-06-23
[QUOTE=aysiu]Reversing the steps: ```
sudo umount /dev/hdc1
sudo rmdir /documents
sudo cp /etc/fstab.backup /etc/fstab
sudo mount -a
```[/QUOTE]

Cheers for the excellent help, all back to what is was.

I love this OS, learning new stuff every day, reminding me of the old, old MS-DOS days 20+ years back.

As I mentioned earlier, have to live with the inability for software such as Azureus to create files on FAT32 systems.

I wonder if it is worth re-formatting one of the external HDD partitions from FAT32 to ext3 would be the way to go, then setting that with full permissions for my use?

Next Q...How is that done? :)

Sorry about all the questions. Been using PC's for 26 years now and feeling like it is only 3!

---

### Post by aysiu on 2006-06-23
You know, that's exactly what I'm thinking. I'm wondering if maybe there's something in the way that Azureus creates files that requires Linux permissions.

You could easily carve an Ext3 partition out of your FAT32 drive (you wouldn't even have to reformat the entire drive) and use that little partition just for Azureus downloads.

```
sudo aptitude update
sudo aptitude install gparted
sudo umount /dev/hdc1
gksudo gparted
``` Right-click to resize. Right-click on the empty space to create. Then [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)

---

### Post by sabredog on 2006-06-23
[QUOTE=aysiu]You know, that's exactly what I'm thinking. I'm wondering if maybe there's something in the way that Azureus creates files that requires Linux permissions.

You could easily carve an Ext3 partition out of your FAT32 drive (you wouldn't even have to reformat the entire drive) and use that little partition just for Azureus downloads.

```
sudo aptitude update
sudo aptitude install gparted
sudo umount /dev/hdc1
gksudo gparted
``` Right-click to resize. Right-click on the empty space to create. Then [http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html)[/QUOTE]


Excellent. I will give that a try shortly.

I assume I run the mount command again after using gparted?

---

### Post by aysiu on 2006-06-23
Yes. You just can't resize or delete partitions that are mounted.

---

### Post by sabredog on 2006-06-23
[QUOTE=aysiu]Yes. You just can't resize or delete partitions that are mounted.[/QUOTE]

Beaut!

Can gparted deal with external/USB HDD's as well?

---

### Post by aysiu on 2006-06-23
Yes, but you have to click on the upper-right corner to see other drives.

---

### Post by sabredog on 2006-06-23
[QUOTE=aysiu]Yes, but you have to click on the upper-right corner to see other drives.[/QUOTE]

reformatted one of the partitions to ext3 and Azureus still refuses to save on anyother location bar the home folder.

Thanks for the gparted assist, learned a lot about how to format a HDD. All good stuff.

I think we are chasing a goose somehow :(

---

### Post by aysiu on 2006-06-23
Maybe you could symlink the Ext3 partition to a folder within your home folder?

For example, if your new Ext3 partition is mounted at /azureus, you could do this: ```
ln -s /azureus ~/azureus
```

---

### Post by sabredog on 2006-06-23
That might work.

Here is the run down so far.

I have an external usb connected HDD now in 2 partitions.
FAT32 19Gb label EXTERNAL-01 mountname EXTERNAL-01
EXT3 18GB mountname usbdisk

These are automounted by dapper and are not seperate entries in fstab.

Should they be?

root owns the new ext3 drive. Can I change that to user ownership ala home folder as that could fix the issue?

can I change the mountname to something more descriptive than usbdrive?

many thanks for all the help. I like to learn, which is why I am FINALLY getting into Linux

---

### Post by aysiu on 2006-06-23
[http://www.psychocats.net/ubuntu/mountlinux.html](http://www.psychocats.net/ubuntu/mountlinux.html) should get your Ext3 drive in order.

And, yes, you can change the mount name to whatever you want, as long as the mount point (folder) exists, and there's an entry in your /etc/fstab for it.

---

### Post by sabredog on 2006-06-23
Crikey! I have file creation!!!

I changed ownership of the new ext3 partition to little old me and Azureus can create a file there now.

I am still a tad confused with one thing though. Can you add a USB drive partition as a permanent mount in fstab? You most excellent guide discusses internal HDD's not External so I am a little unsure if it would work or not. 

I also tried changing the folder name usbdrive and the system would not let me.

---

### Post by aysiu on 2006-06-23
Yes, the same principle applies for internal *and* external hard drives. It's usually just unnecessary for external ones, as those automount.

I wonder why you're having trouble changing the usbdrive name. Basically (assuming your new Ext3 partition is /dev/hdc2), this should work: ```
sudo umount /dev/hdc2
sudo rmdir /media/usbdrive
sudo mkdir /newlocation
``` Then add a line to your /etc/fstab ```
/dev/hdc2 /newlocation ext3 defaults 0 0
```

---

### Post by sabredog on 2006-06-23
[QUOTE=aysiu]Yes, the same principle applies for internal *and* external hard drives. It's usually just unnecessary for external ones, as those automount.

I wonder why you're having trouble changing the usbdrive name. Basically (assuming your new Ext3 partition is /dev/hdc2), this should work: ```
sudo umount /dev/hdc2
sudo rmdir /media/usbdrive
sudo mkdir /newlocation
``` Then add a line to your /etc/fstab ```
/dev/hdc2 /newlocation ext3 defaults 0 0
```[/QUOTE]

Here is a dump of the relevant section from sudo fdisk -l

This shows the old FAT32 partition and the new ext3 partition I created a little while ago using gparted.

```
Disk /dev/sde: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sde2            2551        4846    18442620   83  Linux

```

so I could use /dev/sde2 as part of the new fstab entry?

---

### Post by aysiu on 2006-06-23
Yes, /dev/sde2 would be the new /etc/fstab entry.

---

### Post by sabredog on 2006-06-23
[QUOTE=aysiu]Yes, /dev/sde2 would be the new /etc/fstab entry.[/QUOTE]

Great!

I think this one can be declared a victory then!

Many thanks for your patience and help. I have leaned a lot today.

cheers and thanks again

Mike

---

### Post by FatalAstro on 2006-10-04
[http://ubuntuguide.org/wiki/Dapper#automountntfs]("http://ubuntuguide.org/wiki/Dapper#automountntfs")

This might be helpfull,,im going through it now :)

---

