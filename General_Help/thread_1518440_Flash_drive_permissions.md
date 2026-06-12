---
title: "Flash drive permissions"
date: 2010-06-26
forum: General Help
---

### Post by earther on 2010-06-26
I recently moved to Hardy. My flash drive (vfat) mounts and is readable but I discovered that only root can write to the drive.  I have been all over this forum and Google for days but have not stumbled unto the solution. There seem to be chronic issues with USB devices but none of the solutions quite fit my situation. Maybe something needs to be tweaked in /etc/udev/rules.d/40-permissions.rules?

How can I fix this??  Please help!

---

### Post by Exp HP on 2010-06-26
After mounting it, check the properties of its folder in /media.  Is root the owner of the folder?
On my system, after mounting an SD card or USB memory stick, I'm listed as the owner.

---

### Post by earther on 2010-06-26
> **Exp HP said:**
> After mounting it, check the properties of its folder in /media.  Is root the owner of the folder?
Thanks for responding.  You can see everything is owned by root.  External hard drives are fine.  Just the flash drive is buggy.  Anyone other ideas?

> media/disk$ ls -l
total 72128
drwxr-xr-x 2 root root    16384 2009-02-25 11:11 300inserts
-rwxr-xr-x 1 root root   585811 2009-01-27 11:37 4perry.psd
-rwxr-xr-x 1 root root  2486296 2009-05-26 14:47 600all.jpg
-rwxr-xr-x 1 root root    95592 2009-12-06 14:48 about.jpg
-rwxr-xr-x 1 root root    44053 2009-06-25 16:41 asphalt_invoice.jpg
-rwxr-xr-x 1 root root    21490 2009-06-25 16:44 asphalt.jpg
-rwxr-xr-x 1 root root    12541 2010-05-21 22:47 Bash
-rwxr-xr-x 1 root root 25142060 2008-11-21 18:33 bluefinal.psd
-rwxr-xr-x 1 root root  1492007 2010-05-28 20:33 bookmarks.bak
-rwxr-xr-x 1 root root  1492007 2010-05-28 20:33 bookmarks.html
-rwxr-xr-x 1 root root   508408 2008-09-18 19:56 dunebright.jpg
-rwxr-xr-x 1 root root   451332 2008-09-13 17:53 dune.jpg
drwxr-xr-x 5 root root    16384 2010-02-23 16:09 favicons
drwxr-xr-x 7 root root    16384 2009-01-13 17:30 hardy
-rwxr-xr-x 1 root root 39122611 2008-09-15 22:28 hardy_apt.tar.gz
drwxr-xr-x 2 root root    16384 2010-06-22 15:08 labels
-r-xr-xr-x 1 root root  1110016 2007-02-13 03:33 LaunchU3.exe
-rwxr-xr-x 1 root root   834009 2007-08-08 18:03 logo_plain.psd
drwxr-xr-x 2 root root    16384 2010-06-02 22:01 lucid
-rwxr-xr-x 1 root root    86606 2009-12-06 14:45 pipe_trench.jpg
-rwxr-xr-x 1 root root     1801 2009-08-09 17:03 remote.txt
-rwxr-xr-x 1 root root   124834 2009-12-06 14:47 strike_water.jpg
drwxr-xr-x 3 root root    16384 2010-05-29 14:24 System
drwxr-xr-x 5 root root    16384 2010-06-02 22:03 transfer

---

### Post by Exp HP on 2010-06-26
Have you seen this topic yet? This user managed to get access for the plugdev group on his flash drive.
[http://ubuntuforums.org/showthread.php?t=372435](http://ubuntuforums.org/showthread.php?t=372435)
I think the first user account is in the plugdev group by default, but if not, you could add yourself in System>Administration>Groups and Users.


I'm not sure why root owns your flash drive.  Mine and all files in it are owned by me, and the same holds true for all my digital media. Though I guess it's worth noting that the last time I formatted mine, I did so from Windows.

---

### Post by earther on 2010-06-26
Alas . . . I have tried before to change the owner/group of 'media/disk and it's a no go as was this attempt.

```
~$ sudo chown root:plugdev /media/disk
chown: changing ownership of '/media/disk': Operation not permitted
```

I do appreciate the suggestion though.  I still have a feeling something needs fixing in /etc/udev/rules.d/40-permissions.rules but I don't know quite what.

---

### Post by garvinrick4 on 2010-06-26
Label your USB drive in gparted or disk utility.

Make a directory for it (will be in file system/media)

```
sudo mkdir /media/(usb label)
``````
sudo chown -R rick:rick /media/(usb label)
```rick being your login name.

Will give you permissions on that device.

Such as:
```
sudo mkdir /media/potato
``````
sudo chown -R rick:rick /media/potato
```

Now my USB flash drive named potato can be accessed and read and write.

---

### Post by garvinrick4 on 2010-06-26
Watch out with the chown command can get you into a lot of trouble trying to screw around in places that would be better off left alone. I know as of what I speak as I have had to reinstall a few times at 4:00 AM after a night of chowning around.

---

### Post by garvinrick4 on 2010-06-26
> **5replica said:**
> My flash drive mounts and is readable too,what can i do What do you want to do? Are you just readable and cannot write? Do you
have a label on the device and a what is your login name? Just have to change permissions.

---

### Post by earther on 2010-06-26
> **garvinrick4 said:**
> Will give you permissions on that device.

Such as:
```
sudo mkdir /media/potato
``````
sudo chown -R rick:rick /media/potato
```

Now my USB flash drive named potato can be accessed and read and write.
I know I tried this before but gave it another shot.  I created the folder /media/disk with user permissions.  Plugged in the drive. It just ignored the folder I created and mounted on '/media/disk-1' with root permissions.  So back to square one. I've been going in circles with this for days.  There's GOT to be a way to fix this . . .

---

### Post by garvinrick4 on 2010-06-27
You can open up root in GUI and change permissions.

Alt/F2 and type gksudo nautilus and enter.

If the USB is plugged in you can choose it in root and go to File system to Media.
Right click on your /disk (label) go to properties  and change permissions.

---

### Post by earther on 2010-06-27
> **garvinrick4 said:**
> You can open up root in GUI and change permissions.

If the USB is plugged in you can choose it in root and go to File system to Media.
Right click on your /disk (label) go to properties  and change permissions.
That's exactly what I did.  It won't work - root keeps getting 'permission denied' when it tries to make the change.  AAAARRRGGGH!  And even if it could be changed, next time the drive is mounted, it would have to be done again.  This needs to get fixed at a deeper level.

---

### Post by garvinrick4 on 2010-06-27
Are you making your own folder or making a folder (directory) by using code.
Try making a new label say "broken" and make a new directory.
```
sudo mkdir /media/broken
```

While it is in but not mounted go into disk utility and click on drive and
the on Edit Label and change to broken. Then do the mkdir thing and then do the.

```
sudo chown -R rick:rick /media/broken
```

rick being your login name.
One more shot, cannot understand why it is not changing to your login name.

You have valuable stuff on Flash drive?

---

### Post by earther on 2010-06-27
Oh, I can make a folder in /media and set the owner and user.  That's not the problem.  The disk wants to mount on /media/disk.  If that folder is created with proper permissions, it is just ignored and and new folder /media/disk-1 with root permissions is created at mount.  Interesting thing is that I don't have to be root to umount the drive!

Yeah, I should probably try reformatting next.

Appreciate your continuing to try to sort this out.

---

### Post by Morbius1 on 2010-06-27
Why not just mount it through fstab:

```
 UUID=C4DB-C1B0 /media/disk vfat user,umask=007,utf8,flush,noauto 0 0
```You already created the /media/disk mountpoint. To find the correct UUID for that device:

Make sure the device is plugged in and issue the following command:
```
sudo blkid -c /dev/null
```This is a workaround not a solution. The system should be mounting the device with access to you automatically.

Permissions and ownership of Windows filetypes is done at time of mount. Chown or chmod will have no affect on this type of filesystem.

---

### Post by earther on 2010-06-27
> **Morbius1 said:**
> Why not just mount it through fstab:

```
 UUID=C4DB-C1B0 /media/disk vfat user,umask=007,utf8,flush,noauto 0 0
```You already created the /media/disk mountpoint. To find the correct UUID for that device:

Make sure the device is plugged in and issue the following command:
```
sudo blkid -c /dev/null
```This is a workaround not a solution. The system should be mounting the device with access to you automatically.
OMG!! This seems to be working!!  You are my hero!!!

The question is . . .

WHY isn't it mounting automatically with the correct permissions?  There should be a way to fix this somewhere in /etc.  I keep coming back to /etc/udev/rules.d/40-permissions.rules but I don't know enough to try to write a rule from scratch.  [**This tutorial**]("http://ubuntuforums.org/showthread.php?t=168221") looks promising . . .

---

### Post by earther on 2010-06-27
Forgot to mention that before I tried the above, I reformatted the drive.  It made no difference.  It still was mounting as root.

---

