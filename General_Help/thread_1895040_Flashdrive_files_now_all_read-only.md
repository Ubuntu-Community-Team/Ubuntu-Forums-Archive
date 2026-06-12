---
title: "Flashdrive files now all read-only??"
date: 2011-12-13
forum: General Help
---

### Post by chuangt2u on 2011-12-13
Hi.
I'm looking for a little help with an unusual problem with my usb flashdrive.

All of the files it contains have changed permissions to read-only... I can't edit, delete, or cut any of them.

When I try to do the above with .doc or .odt files, I get a message saying "file locked for editing by unknown user", and a choice of opening the file as read-only, as a copy, or canceling the operation. When opened as a copy, a file can be saved to my computer with no further problems, but if saved to the flashdrive - the permissions problem restarts with the new file.

I'm a teacher, and have most of my materials on this flash drive, so this is causing quite a problem.

Does anyone have an idea as to what's going on and how I can fix it?

Using Natty, not the listed Lucid on the left, there... can't get permission to edit that either... permissions, permissions.

Many thanks

C

---

### Post by LowSky on 2011-12-14
open nautilus using sudo by opening a terminal and typing sudo nautilus

then go to the files on the flash drive, right click then go to properties. one of the tabs is permissions, set the owner to you, and the device to read/write

---

### Post by chuangt2u on 2011-12-14
Thanks for your reply!

I tried that, but I'm already set as the owner. The files are set as read only, and if I try to change the file permissions, I get the message:

> Sorry, could not change the permissions of "Eve.doc": Error setting permissions: Read-only file system

 - Any ideas why it doesn't work?

Through nautilus, I can't change file permissions or reset the permissions for the flashdrive (pendrive); here's the commentary in terminal:

> rmation for process '1918'

(nautilus:1918): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
**Please ask your system administrator to enable user sharing**.


Error: Couldn't open file '/media/PENDRIVE/Home/kuklinski.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/media/PENDRIVE/Home/nyhan-reifler.pdf': Permission denied.
Error loading document: Error opening file: Permission denied
Error: Couldn't open file '/media/PENDRIVE/Home/School/700 Classroom activities.pdf': Permission denied.
Error loading document: Error opening file: Permission deniedIt's my home box, I'm the system administrator, and I haven't changed any settings.

---

### Post by jimmydean886-2 on 2011-12-14
> **chuangt2u said:**
> Thanks for your reply!

I tried that, but I'm already set as the owner. The files are set as read only, and if I try to change the file permissions, I get the message:



 - Any ideas why it doesn't work?

Through nautilus, I can't change file permissions or reset the permissions for the flashdrive (pendrive); here's the commentary in terminal:

It's my home box, I'm the system administrator, and I haven't changed any settings.
Try going to each file and setting the permissions manually. It takes forever, but it should work.

---

### Post by chuangt2u on 2011-12-14
Thanks, JD - I tried that, but got the message:

> Sorry, could not change the permissions of "Eve.doc": Error setting permissions: Read-only file system

Seems I'm locked out of my USB re editing, deleting, cutting and pasting documents.

---

### Post by Jay Car on 2011-12-14
> **chuangt2u said:**
> Seems I'm locked out of my USB re editing, deleting, cutting and pasting documents.

> **LowSky said:**
> open nautilus using sudo by opening a terminal and typing sudo nautilus

then go to the files on the flash drive, right click then go to properties. one of the tabs is permissions, set the owner to you, and the device to read/write

LowSky, wouldn't the use of 
```
gksudo nautilus
``` 
work better? I remember encountering a similar problem with permissions a few years ago, using gksudo nautilus helped me to fix it. 

Also, while in Nautilus, right-clicking on a folder, choosing properties, then the permissions tab, allows you to set read, write, and execute permissions on those files. 

chuangt2u, Hopefully this method will work for you too. 

:)

---

### Post by strafe_sawdoffe on 2011-12-15
Happened to me once... at the time I had less than 1GB on it though, so I copied everything to a temp directory in my home folder, formatted the flash drive, and copied everything back; fixed it. Is that an option for you?

---

### Post by greenfrog on 2011-12-15
Try putting the Flashdrive in a different USB port, I found out that one of my ports was not putting out the right voltage and I was getting the same problem, switched to a different port and all was well.

---

### Post by ottosykora on 2011-12-15
can you see if you have program usbmount installed?

There used to be some issues in this direction with it. Uninstall of this usbmount did sometimes (as in my case) cure this problem.

---

### Post by rng on 2011-12-15
What format is usb?

Changing ownership might help: 

```
chown -Rc username:username /media/somedrive
```

---

### Post by coffeecat on 2011-12-15
@chuangt2u, we need to see what filesystem is on these drives that are read-only, and how they are being mounted. Plug one of the drives in, let it be automounted and then post the output of this terminal command:

```
mount
```

And as ottosykora suggests, make sure you don't have the app usbmount installed. It is designed for GUI-less systems and interferes with the automounting functionality in desktop versions of Ubuntu.

---

### Post by chuangt2u on 2011-12-15
Thanks for all the help - here's what happened...

@Jay Car
```
gksudo nautilus
```
This allowed me to change the permissions from the properties tab, but although I changed both owner and group permissions to read+write, only the owner permissions were stored. Somehow, even with owner permissions set and to read+write, I still can't open the documents as anything other than read only.

@greenfrog
> Try putting the Flashdrive in a different USB port
Thanks, but that didn't work.

@ottosykora
Synaptic says I don't have usbmount installed... but I'll remember it.

@rng
```
chown -Rc username:username /media/somedrive
```
This changed the ownership of a huge list of files, but after each notification of change, there was a note that it's a read-only file system...

> chown: changing ownership of `/media/PENDRIVE/*my school*/E1 occupations/photo-782824.JPG': Read-only file system

@coffeecat
```
mount
```
gave this

> /dev/loop0 on / type ext4 (rw,errors=remount-ro,user_xattr,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
/dev/sda1 on /host type fuseblk (rw,nosuid,nodev,relatime,user_id=0,group_id=0,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/*user*/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=*user*)
/dev/sdb1 on /media/PENDRIVE type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)
gvfs-fuse-daemon on /root/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev)

@strafe_sawdoffe
I do happen to have less than 1gb left on the flashdrive - and will be trying the transferring of files to my box and formatting the flashdrive next. That will take some time, so I'll post back here when it's done.

Thanks for your help, everyone.

C

---

### Post by coffeecat on 2011-12-15
This is the important bit:

> **chuangt2u said:**
> ```
/dev/sdb1 on /media/PENDRIVE type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000, shortname=mixed,dmask=0077,utf8=1,showexec,flush)
```

You have a vfat (probably FAT32 or FAT16) filesystem on that particular drive, which is a Microsoft filesystem, which does not support the Linux system of permissions and ownership. Which means that trying to change ownership or permissions with chown, chmod or nautilus (even if opened with gksu) will not work. Ownership and permissions are set with the mount options, which are listed above. That line tells us two things. You don't have usbmount installed (wrong mountpoint), and the drive has been mounted read-write, even though you can't write to it.

One thing you might try is to check the filesystem from Windows, and then unmount it cleanly. If a filesystem is damaged, Ubuntu will mount it read-only, although if that were the case here I would have expected "ro" in those mount options, not "rw".

---

### Post by chuangt2u on 2011-12-15
Ok. So it's an MS problem?

> One thing you might try is to check the filesystem from Windows, and then unmount it cleanly.

I don't have Windows at home, so can't try that one.

When I reformat the drive, is there a specific way to do it that will make the drive more Linux friendly? - I'll be doing it from Natty.

---

### Post by rng on 2011-12-15
You can copy all files to the hard disk and format the usb flashdrive. Then copy back the files to it. It may work.

---

### Post by chuangt2u on 2011-12-15
> You can copy all files to the hard disk and format the usb flashdrive. Then copy back the files to it. It may work. 	

That did it CHEERS!

---

