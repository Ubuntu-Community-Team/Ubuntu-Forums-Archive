---
title: "ARGHHHHH! Filesystem mounting help please."
date: 2006-02-27
forum: General Help
---

### Post by samwh on 2006-02-27
Could someone PLEASE just give me the fstab options to get the following:

A READ ONLY partition, mounted at boot up, mountable and accessable by all users

A Read/write partition, mounted at boot up, mountable, readable, writable by all users

And 2 cd burners, accessable by all users

1 floppy drive, accessable by all users.

Thanks, I have been screwing around with FSTAB options all afternoon, none will fully work.

Thanks,
Sam

---

### Post by ykpaiha on 2006-02-27
arghhhh, before shouting U could explain your prob in a right way:
wich partion 
what is your fstab
wich file system you are talking about.
Then have you noticed there is some tools in this forum 
One is very usefull it called search it will answer at least 100 time your question...
:p :p :p :p

---

### Post by samwh on 2006-02-27
Yeah, sorry.

I already did search... my partitions are:

One NTFS (need a ro, mount on boot)
One fat32 (need a RW, mount on boot)
Floppy (need a RW, automount)
DvdROM (need RO, automount)
DVDRW (need RO, automount, burning w/ all users)

ALL of the above needs to be mountable, readable, writeable, and unmountable.

Sorry for shouting :-#

---

### Post by ykpaiha on 2006-02-27
no don't be just take advantage of the forum,:rolleyes: 

here is my own fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               reiserfs notail          0       1
/dev/hdb2       /home           reiserfs defaults        0       2
/dev/hda1       /media/hda1     ntfs   ro,user,auto,gid=100,nls=utf8,umask=002     0       0
/dev/hda2       /media/hda2     vfat   rw,user,auto,gid=100,uid=1000,umask=002,iocharset=utf8,codepage=850        0       0
/dev/hdb3       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda        /media/usb0     auto    rw,user,noauto  0       0


vfat read writable
ntfs just read
floppies and cds, dvd own by user with an automatic file system (usualy,iso,vfat,ext3etc...)
 I hope that's help.
then:
sudo mount -a 
will mount all accessible media from Ur fstab you can cornect it easly

you can as well read this:
[http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only](http://easylinux.info/wiki/Ubuntu#How_to_mount_Windows_partitions_.28NTFS.29_on_boot-up.2C_and_allow_all_users_to_read_only)

---

### Post by z_diver on 2006-02-27
[QUOTE=samwh]Could someone PLEASE just give me the fstab options to get the following:

A READ ONLY partition, mounted at boot up, mountable and accessable by all users

A Read/write partition, mounted at boot up, mountable, readable, writable by all users

And 2 cd burners, accessable by all users

1 floppy drive, accessable by all users.

Thanks, I have been screwing around with FSTAB options all afternoon, none will fully work.

Thanks,
Sam[/QUOTE]
fstab handles a LOT of variables such as what type of disk drive, which disk number and what partition has what type of filesystem to use.  

We'll need a lot more info before being able to write the table you are requesting accurately but i'll give it a (f)stab in the dark. :D 

For the cdroms use: (unless there are more than 2 hard drives connected)
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0

For the floppy use:
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

I'm guessing you had a windows install of some sort originally and want read only access to it.  If it was an ntfs partition on the first ide drive you might use something like:
/dev/hda1    /windows/C      ntfs noauto,ro,users,gid=users,nls=utf8    0   0

If your system is booting you can safely use whatever was set to use the / partition.  Probably also had an ext3 partion on it if you did a default install.

For the swap partition use: (swapping the * with partition number)
/dev/hda*       none            swap    sw              0       0

and this is standard for the top line:
proc            /proc           proc    defaults        0       0

---

### Post by samwh on 2006-02-27
Thanks guys, that just what I was looking for ;)

---

### Post by samwh on 2006-02-27
Is there a way to give all permissions (read, write) to a partition (my fat32 music partition, /dev/hda2, keep getting access denied errors when not sudo)

---

### Post by Mustard on 2006-02-27
[QUOTE=samwh]Is there a way to give all permissions (read, write) to a partition (my fat32 music partition, /dev/hda2, keep getting access denied errors when not sudo)[/QUOTE]

At the moment you are still asking people to shoot in the dark with regards to answering your question.  What is needed is for you to paste the actual contents of your /etc/fstab file into this thread, so we can see what you have in there already.

You could also paste in the output of his command too...

```
sudo fdisk -l
#this command will list all your partitions and information about them

cat /etc/fstab
#this will display the contents of your fstab file, so this one too
```

Enclose the output of these in these forum codes for neatness [noparse]```
...your text in here...
```[/noparse]

---

### Post by ykpaiha on 2006-02-27
right clic properties on the folder and check it's rights!!!
if not suitable for you 
sudo chmod -R 755
on this folder will change all the right on it and all subs as well.
this as well you can fin it here 

[http://easylinux.info/wiki/Ubuntu](http://easylinux.info/wiki/Ubuntu)

just time to ....look

---

### Post by ykpaiha on 2006-02-27
[QUOTE=Mustard]At the moment you are still asking people to shoot in the dark with regards to answering your question.  What is needed is for you to paste the actual contents of your /etc/fstab file into this thread, so we can see what you have in there already.

You could also paste in the output of his command too...

```
sudo fdisk -l
#this command will list all your partitions and information about them

cat /etc/fstab
#this will display the contents of your fstab file, so this one too
```

Enclose the output of these in these forum codes for neatness [noparse]```
...your text in here...
```[/noparse][/QUOTE]

thanks for your support lol\\:D/

---

