---
title: "Can't read NTFS drive"
date: 2006-06-05
forum: General Help
---

### Post by Soup4Brains on 2006-06-05
I'm perfectly aware that NTFS drives are supposed to be read-only in Ubuntu, but I can't even read the contents of the drive without getting this error:

You do not have the permissions necessary to view the contents of "disks-conf-sda1".

How can I make the drive read-only (so as not to screw up my Windows XP installation somehow) while still being able to view and open the contents of the drive, such as listen to my music?

Thanks in advance.

---

### Post by .t. on 2006-06-05
This is to do with the drive being mounted in a directory that only root can read, with root-read-only permissions on the drive. I have this problem sometimes, so I sudo chmod --recursive aoug+r <folder> and sudo chown --recusive <user:group> <folder>. Also look at your /etc/fstab (type man mount/man fstab for more info).

---

### Post by Soup4Brains on 2006-06-05
Could you please tell me exactly what those commands do before I use them? I'm pretty new to the Linux command line and I'm really nervous about killing my Windows disk.

---

### Post by caldevil on 2006-06-05
[QUOTE=Soup4Brains]I'm perfectly aware that NTFS drives are supposed to be read-only in Ubuntu, but I can't even read the contents of the drive without getting this error:

You do not have the permissions necessary to view the contents of "disks-conf-sda1".

How can I make the drive read-only (so as not to screw up my Windows XP installation somehow) while still being able to view and open the contents of the drive, such as listen to my music?

Thanks in advance.[/QUOTE]
Can you post the content of /etc/fstab?

---

### Post by Soup4Brains on 2006-06-05
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by Tekk on 2006-06-05
Sorry to butt in, but I'm trying to do pretty much the same thing to no avail. I ran the above commands and it shot through the "changing ownership of yadayada," for every file on the partition. Appended to the end of each of those lines, however, is "Read-only file system." 

Is it telling me that it isn't working? I ask because it didn't, as can be seen from a quick 'ls -l' ... All files still belong to root and cannot be accessed.

---

### Post by caldevil on 2006-06-05
[QUOTE=Soup4Brains]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdd1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdd5       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0[/QUOTE]
What you can do is:

mkdir /mnt/windows

and add the following line to your /etc/fstab

/dev/hda2       /mnt/windows  ntfs    umask=022       0       0

where /dev/hda2 is the device for your windows partition (if you don't know the device, you can run "sudo fdisk -l" to see that).
unmask=022 take care of the drive being readable by all users.

After that you can either restart your computer and windows would be automounted on /mnt/windows or run "sudo mount /mnt/windows".

---

### Post by CronoDekar on 2006-06-05
What you basically have to do is unmount the partition, and remount it in another place.  For some reason when it's not in your fstab it seems to be mounted to where you can't get to it.  From terminal, do:

sudo umount /dev/hda1 
Replace /dev/hda1 with whichever device your NTFS is, see System > Administration > Disks.

sudo mkdir /media/windows
This creates a directory that you'll mount your NTFS partition from.

sudo mount /dev/hda1 /media/windows/ -t ntfs -o umask=0222
Again, replacing /dev/hda1 with what the Disk manager tells you it is.  This mounts it in /media/windows so you can open it (though you should only need to go to Filesystem to get to it).

If you want it to mount your NTFS partition normally when you boot the computer, see this link:

[https://wiki.ubuntu.com/MountNtfsOnBoot](https://wiki.ubuntu.com/MountNtfsOnBoot)

Note that while it uses /mnt/ntfs1, you can still use /media/windows, or any other empty folder if you so choose.

---

