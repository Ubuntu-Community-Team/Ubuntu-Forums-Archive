---
title: "USB stick read as &quot;read only&quot; when its not."
date: 2010-11-15
forum: General Help
---

### Post by Jotaro on 2010-11-15
Well here is what happened.
I plugged the USB stick in, and it mounted successfully. Then, I deleted some of the stored music files on the stick, and sent them to my recycle bin. I tried to empty my recycle bin, but it wouldn't let me. Then, I tried to place new music files on the stick, but I got the error "The destination is read only", but its not. Now, even when I unmount it and remount it, it keeps giving me the same error regardlessly. Can anyone help me?

---

### Post by pqwoerituytrueiwoq on 2010-11-15
what format is the drive
fat32/ntfs/ext3/ext4

---

### Post by Jotaro on 2010-11-15
Its brand is a "patriot memory" 4 GB
I don't know where I would need to look to find out which format it is.

---

### Post by ppv on 2010-11-15
How do you mount/unmount it.

---

### Post by Jotaro on 2010-11-15
I right click it on the menu and choose either "Eject" or "Safely Remove Drive"

---

### Post by ppv on 2010-11-15
> **Jotaro said:**
> I right click it on the menu and choose either "Eject" or "Safely Remove Drive"

Does plugging out and then plugging in the drive again work.

---

### Post by Jotaro on 2010-11-15
> **ppv said:**
> Does plugging out and then plugging in the drive again work.
I unplug it and plug it back it. It senses it and it comes up like normal, but still when I try to put a music file on it, it says "Error: Destination is Read Only"
So no, unplugging and plugging it back it doesn't fix the problem.

---

### Post by Jotaro on 2010-11-15
I just found out the type it is, which is called "Compatible with all systems (FAT)

---

### Post by ppv on 2010-11-15
Does your drive have a small toggle switch that write-protects the device. Do you have another system where you can try the drive.

---

### Post by Jotaro on 2010-11-15
I can go to "Format" and then "Disk Utility" and it tells me a lot of stuff.
No, I do not have another computer to test it on.
No, it doesn't have a switch that can be toggled off or on when it comes to protecting the device.

---

### Post by ppv on 2010-11-15
With the drive plugged in, can you put in the output of the mount command as well as the contents of /etc/fstab.

---

### Post by Jotaro on 2010-11-15
> **ppv said:**
> With the drive plugged in, can you put in the output of the mount command as well as the contents of /etc/fstab.
What is the mount command?
Also, where will I find etc/fslab at?

---

### Post by ppv on 2010-11-15
At the command prompt type mount and hit enter.
To see the contents of /etc/fstab, type cat /etc/fstab at the command prompt and hit enter.

---

### Post by Jotaro on 2010-11-15
> **ppv said:**
> At the command prompt type mount and hit enter.
To see the contents of /etc/fstab, type cat /etc/fstab at the command prompt and hit enter.
Ok, I opened a window for the terminal.
I typed Mount and entered it. This is what I got:

/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
gvfs-fuse-daemon on /home/me/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=me)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/dev/sdb1 on /media/UDISK 2.0 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

I typed and entered cat/etc/fstab, and it gave me this:
bash: cat/etc/fstab: No such file or directory

---

### Post by col48 on 2010-11-15
ppv meant 
cat /etc/fstab
with a space after cat.

This lists the contents of the file.

---

### Post by Jotaro on 2010-11-15
> **col48 said:**
> ppv meant 
cat /etc/fstab
with a space after cat.

This lists the contents of the file.
Oh, I see. I entered cat /etc/fstab and got this:

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=dd024469-2ece-461f-a3ee-f3bf67a2f25a /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=f9e5b7c5-fa0f-41a0-978d-ca1e1fd09f9e none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by Jotaro on 2010-11-15
Well since this has fallen off the first page, I am allowed to bump it.
So bump.

---

### Post by Jotaro on 2010-11-15
Well since this has fallen off the first page I am allowed to bump it.
So bump.

---

### Post by yetiman64 on 2010-11-15
> **Jotaro said:**
> Well since this has fallen off the first page I am allowed to bump it.
So bump.

Forum guidelines is to bump only once every 24 hours, not when it falls off the first page :).

Have patience, when someone with enough knowledge of mounting FAT partitions sees this they will most likely help. Good luck.

Edit: check out "Don't #8" in [--this post--]("http://ubuntuforums.org/showthread.php?t=885580") for confirmation of guidelines.

---

### Post by Jotaro on 2010-11-15
> **yetiman64 said:**
> Forum guidelines is to bump only once every 24 hours, not when it falls off the first page :).

Have patience, when someone with enough knowledge of mounting FAT partitions sees this they will most likely help. Good luck.

Edit: check out "Don't #8" in [--this post--]("http://ubuntuforums.org/showthread.php?t=885580") for confirmation of guidelines.
Ok, thanks for the advice.

---

### Post by ppv on 2010-11-15
Do you know if your device is /dev/sdb1. If not, you can run Disk Utility or Gparted and that should give you your device name.

If is is /dev/sdb1, from the command prompt execute,

umount /dev/sdb1
mkdir ~/USB_disk
mount /dev/sdb1 ~/USB_disk
mkdir ~/USB_disk/USB_directory

If the last command passes then you could now write to the device.

---

### Post by Jotaro on 2010-11-15
> **ppv said:**
> Do you know if your device is /dev/sdb1. If not, you can run Disk Utility or Gparted and that should give you your device name.

If is is /dev/sdb1, from the command prompt execute,

umount /dev/sdb1
mkdir ~/USB_disk
mount /dev/sdb1 ~/USB_disk
mkdir ~/USB_disk/USB_directory

If the last command passes then you could now write to the device.
Ah, well I have also discovered that I can't delete files in the trash of the device as well.
And yes, it is in fact /dev/sdb1.

I entered what you said and it gave me this:

me@me-desktop:~$ umount /dev/sdb1
me@me-desktop:~$ mkdir ~/USB_disk
me@me-desktop:~$ mount /dev/sdb1 ~/USB_disk
mount: only root can do that
me@me-desktop:~$ mkdir ~USB_disk/USB_directory
mkdir: cannot create directory `~USB_disk/USB_directory': No such file or directory
me@me-desktop:~$

---

### Post by Verbeck on 2010-11-15
> **ppv said:**
> 
**sudo** umount /dev/sdb1
mkdir ~/usb_disk
**sudo** mount /dev/sdb1 ~/usb_disk
mkdir ~/usb_disk/usb_directory

could you try again with that

---

### Post by Jotaro on 2010-11-15
> **Verbeck said:**
> could you try again with that
Wait, so you want me to try each of those four commands seperately?
Or enter all of them as a single command?

---

### Post by yetiman64 on 2010-11-15
> **Jotaro said:**
> Wait, so you want me to try each of those four commands seperately?
Or enter all of them as a single command?

Exactly as you did for ppv's commands (separately) but substitute the  commands posted by Verbeck as they have the necessary sudo prefix to  allow the proper use of mount and umount commands.

Edit: just realized those commands may only be good for a single mount and the next time you reboot the situation may return to your current state. Will make a good test to see if the files become accesible though.

---

### Post by Jotaro on 2010-11-15
Ok, I entered it. This is what I got.

me@me-desktop:~$ sudo umount /dev/sdb1
me@me-desktop:~$ mkdir ~/usb_disk
mkdir: cannot create directory `/home/me/usb_disk': File exists
me@me-desktop:~$ sudo mount /dev/sdb1 ~/usb_disk
me@me-desktop:~$ mkdir ~/usb_disk/usb_directory
mkdir: cannot create directory `/home/me/usb_disk/usb_directory': Read-only file system

---

### Post by yetiman64 on 2010-11-15
> mkdir: cannot create directory `/home/me/usb_disk': File existsThis is OK just means your first attempt succeeded in making the folder in your home folder.

Can you post the contents of /etc/mtab with,
```
cat /etc/mtab | grep vfat
``` this file is used for mounting options on removable devices. The "| grep vfat" is to specify the usb stick.

Mounting seems to be picking up mount options from somewhere and automounting the USB stick as a read only filesystem no matter where it is mounted.

---

### Post by Sven6210 on 2010-11-15
I would format the stick with "fat32" in case you also want the flexibility to use it with windows computers.

In case you only want to use the stick with Ubuntu/Linux you can also consider formatting it with "ext4" (or "ext3"). But keep in mind that normal windows computers will not be able to read it.

Before you format the stick make sure you copy all files you want to keep to your hard-disk. Before you can format a stick you need to unmount it but (obviously) leave it connected with the computer.

Do you know how to format a USB stick?

---

### Post by Jotaro on 2010-11-15
Ok, I entered 
cat /etc/mtab | grep vfat 
and I got this:

me@me-desktop:~$ cat /etc/mtab | grep vfat
/dev/sdb1 /home/me/usb_disk vfat rw 0 0

The vfat part is in red.

As for formatting, when I try to format it, it says this:

"Error formatting drive"
"An error occurred while performing an operation on "USB DISK2.0" (USB DISK2.0): The device is busy"
under options, it gives:
"One or more partitions are busy on /dev/sdb"

---

### Post by yetiman64 on 2010-11-15
> **Jotaro said:**
> Ok, I entered 
cat /etc/mtab | grep vfat 
and I got this:

me@me-desktop:~$ cat /etc/mtab | grep vfat
/dev/sdb1 /home/me/usb_disk vfat rw 0 0

The vfat part is in red.

Red is normal, just highlighting of what you asked for.

Not what I was expecting maybe need to run the mount command again only this time specify the usb stick with,
```
mount | grep vfat
```

---

### Post by Verbeck on 2010-11-15
> **Jotaro said:**
> 
"Error formatting drive"
"An error occurred while performing an operation on "USB DISK2.0" (USB DISK2.0): The device is busy"
under options, it gives:
"One or more partitions are busy on /dev/sdb"
you should unmount it before attempting to format it

sudo umount /dev/sdb1

or use disk utility to unmont and format it (system>administration>disk utility)

---

### Post by Jotaro on 2010-11-15
> **yetiman64 said:**
> Red is normal, just highlighting of what you asked for.

Not what I was expecting maybe need to run the mount command again only this time specify the usb stick with,
```
mount | grep vfat
```
Ok, how to I specify the usb stick?
Do I just enter "mount | insert name of usb stick here" like that?

---

### Post by Jotaro on 2010-11-16
> **Verbeck said:**
> you should unmount it before attempting to format it

sudo umount /dev/sdb1

or use disk utility to unmont and format it (system>administration>disk utility)
Ok, I chose the "Eject" option, then chose "Format Drive"

Error I got back:

"Error formatting drive"
"An error occured while performing an operation on "USB DISK 2.0" (USB DISK 2.0): The operation failed."

Details:
"Error creating partition table: helper exited with exit code 1: cannot open /dev/sdb: No medium found."

---

### Post by yetiman64 on 2010-11-16
> **Verbeck said:**
> you should unmount it before attempting to format it

sudo umount /dev/sdb1

or use disk utility to unmont and format it (system>administration>disk utility)

Jotaro, I just saw this and realized you are trying to format, please hold on as you are getting 2 very different advice streams and it would pay not to cross them together.

I am trying to locate why a vfat partition is being automatically mounted as read only and not trying to format or do anything potentially destructive at this stage.

> Do I just enter "mount | insert name of usb stick here" like that?     Just copy and paste the code in the code box to a terminal, the "| grep vfat" is what is specifying the usb stick.

---

### Post by Jotaro on 2010-11-16
> **yetiman64 said:**
> Jotaro, I just saw this and realized you are trying to format, please hold on as you are getting 2 very different advice streams and it would pay not to cross them together.

I am trying to locate why a vfat partition is being automatically mounted as read only and not trying to format or do anything potentially destructive at this stage.

Just copy and paste the code in the code box to a terminal, the "| grep vfat" is what is specifying the usb stick.
Ok, I will stay with you on trying to figure out why it is mounting incorrectly.
mount | grep vfatI entered this, but it doesn't give me any messages. After I enter it, what should I try to do?
I have it mounted already.

---

### Post by yetiman64 on 2010-11-16
> **Jotaro said:**
> Ok, I will stay with you on trying to figure out why it is mounting incorrectly.
mount | grep vfatI entered this, but it doesn't give me any messages. After I enter it, what should I try to do?
I have it mounted already.

Ok you will need to unmount it from ~,with
> sudo umount ~/usb_disk Go to Places > Computer and find the usb stick, right click it and "Safely remove drive".

If you can totally unmount and safely remove it, physically unplug it then plug it back in. This should use the standard mounting for the usb stick from where you can chase down the mount problem.

Rerun the mount command I gave earlier again, it should give an output based on an earlier post with the mount command in it.

If you decide to format to a different filesystem just remember to copy any contents of the stick to your harddrive with it mounted standard. Even though you only have read access you can back up the contents to your HDD.

Edit: actually this is the previous mount output and is where I suspect the problem to show up,
> /dev/sdb1 on /media/UDISK 2.0 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,   shortname=mixed,dmask=0077,utf8=1,flush)


---

### Post by Jotaro on 2010-11-16
> **yetiman64 said:**
> Ok you will need to unmount it from ~,with
 Go to Places > Computer and find the usb stick, right click it and "Safely remove drive".

If you can totally unmount and safely remove it, physically unplug it then plug it back in. This should use the standard mounting for the usb stick from where you can chase down the mount problem.

Rerun the mount command I gave earlier again, it should give an output based on an earlier post with the mount command in it.

If you decide to format to a different filesystem just remember to copy any contents of the stick to your harddrive with it mounted standard. Even though you only have read access you can back up the contents to your HDD.

Edit: actually this is the previous mount output and is where I suspect the problem to show up,

Ok, I ran it, and it gave this:

me@me-desktop:~$ mount | grep vfat
/dev/sdb1 on /media/UDISK 2.0 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

and the vfat part after type is in red. What should I do next? Also, thank you for helping me so far.

---

### Post by yetiman64 on 2010-11-16
> **Jotaro said:**
> Ok, I ran it, and it gave this:

me@me-desktop:~$ mount | grep vfat
/dev/sdb1 on /media/UDISK 2.0 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)

and the vfat part after type is in red. What should I do next? Also, thank you for helping me so far.

You're welcome Jotaro, however I'm probably pushing the limits of my understanding here at the moment and would have to do a lot of research / googling to work this one out. **Hopefully some more knowledgeable user will pop in soon and help out** :). 

From what I'm seeing the options for read/write (rw), user id (uid) and group id (gid) are OK providing you are user 1000 (this can be checked via System > Administration > Users and Groups > Manage Groups, In group settings locate your username and highlight it and click Properties. 

Darn, just found a quicker way in terminal to check user 1000.
> cat /etc/passwd | grep 1000 **Use it to check but I suggest not posting it here**, as it contains your username, possibly your real name and uid and gid (privacy concerns).

That dmask entry has me baffled and will need to be checked.

If you have no problems with the filenames / contents of your usb stick being seen could you post the output of,
```
ls -l /media/"UDISK 2.0"
``` If you have any privacy or nsfw concerns replace a foldername or filename in the output with "censored" as it is the permissions/ownership of files/folders here I'm interested in.

Also with the stick mounted as standard (as it now is) please repost,
```
cat /etc/mtab | grep vfat
```

---

### Post by Jotaro on 2010-11-16
> **yetiman64 said:**
> You're welcome Jotaro, however I'm probably pushing the limits of my understanding here at the moment and would have to do a lot of research / googling to work this one out. **Hopefully some more knowledgeable user will pop in soon and help out** :). 

From what I'm seeing the options for read/write (rw), user id (uid) and group id (gid) are OK providing you are user 1000 (this can be checked via System > Administration > Users and Groups > Manage Groups, In group settings locate your username and highlight it and click Properties. 

Darn, just found a quicker way in terminal to check user 1000.
 **Use it to check but I suggest not posting it here**, as it contains your username, possibly your real name and uid and gid (privacy concerns).

That dmask entry has me baffled and will need to be checked.

If you have no problems with the filenames / contents of your usb stick being seen could you post the output of,
```
ls -l /media/"UDISK 2.0"
``` If you have any privacy or nsfw concerns replace a foldername or filename in the output with "censored" as it is the permissions/ownership of files/folders here I'm interested in.

Also with the stick mounted as standard (as it now is) please repost,
```
cat /etc/mtab | grep vfat
```
I just entered:
cat /etc/passwd | grep 1000                      

It gave me this:
me:x:1000:1000:me,,,:/home/me:/bin/bash
The two 1000 are in red.

The contents:
total 788
-rwxr-xr-x 1 me me 803673 2007-08-18 02:09 setup.exe
Setup is in green. Reason for the total = I deleted the contents of the usb in the beginning, but it won't let me empty the trash bin for it.

Ok, entering this:
cat /etc/mtab | grep vfat

Gives me this:

/dev/sdb1 /media/UDISK\0402.0 vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0

Again, with the vfat part in red.

---

### Post by ppv on 2010-11-16
it could be the dmask value...umask for directories.

the permissions are set as default-umask...777-077...700. 

could you set the dmask to 0000 and see if it works. you may have to edit the dmask value in mtab.

---

### Post by yetiman64 on 2010-11-16
Your uid and file ownership and permissions all seem OK, so it does seem to be a mounting option problem. 

The only thing I can pick is the dmask value, but will need to check around a bit before going any further, I'll be back ASAP.

---

### Post by Jotaro on 2010-11-16
> **ppv said:**
> it could be the dmask value...umask for directories.

the permissions are set as default-umask...777-077...700. 

could you set the dmask to 0000 and see if it works. you may have to edit the dmask value in mtab.
Ok, how do I set the dmask to 0000?
How to I reach mtab?

---

### Post by Jotaro on 2010-11-16
> **yetiman64 said:**
> Your uid and file ownership and permissions all seem OK, so it does seem to be a mounting option problem. 

The only thing I can pick is the dmask value, but will need to check around a bit before going any further, I'll be back ASAP.
Ah, ok. I can wait.

---

### Post by yetiman64 on 2010-11-16
Just found the following on a LinuxQuestions.org thread regarding FAT32 and am reasonably confident it applies to FAT as well,
>  Even if a different user mounts a fat32 partition, the uid=, gid=,  fmask= and dmask= options will determine whether that user can read or  write.  
Try changing the dmask value with,
```
gksudo gedit /etc/mtab
``` highlight the 77 in "dmask=0077" in the appropriate line and replace with 00, so you end up with "dmask=0000". Save the file, unmount and safely remove the usb stick, reinsert the usb stick and check the mount again with,
```
mount | grep vfat
```If the dmask value is 0000 then try to clean out the trash or create / delete items etc as you originally tried to. Hoping this will work this time.

---

### Post by Jotaro on 2010-11-16
> **yetiman64 said:**
> Just found the following on a LinuxQuestions.org thread regarding FAT32 and am reasonably confident it applies to FAT as well,
Try changing the dmask value with,
```
gksudo gedit /etc/mtab
``` highlight the 77 in "dmask=0077" in the appropriate line and replace with 00, so you end up with "dmask=0000". Save the file, unmount and safely remove the usb stick, reinsert the usb stick and check the mount again with,
```
mount | grep vfat
```If the dmask value is 0000 then try to clean out the trash or create / delete items etc as you originally tried to. Hoping this will work this time.

Ok, I went into mtab, and changed where it said "dmask=0077" into "dmask=0000"
I clicked "Save" at the top, then clicked "eject". It asked if I wanted to empty the trash bin before I eject, and I clicked "yes" Then, I went to computer and clicked the device and selected "Safely remove".

I plugged it back in, and using the terminal after entering the other code, it gave me this:

/dev/sdb1 on /media/UDISK 2.0 type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush)
Again, with vfat in red.

I tried to delete only one item from the trash permanently, and it said the same error again.

---

### Post by yetiman64 on 2010-11-16
Ok, that's not good, the dmask value (0000) didn't hold on re-inserting the usb stick -- that is the problem continues the same.

The dmask value is the only thing I can see for blocking rw access.

I will continue looking around, but if anyone else has ideas for setting the dmask value on removable usb drives to 0000 temporarily they would be worth looking into.

---

### Post by Jotaro on 2010-11-16
> **yetiman64 said:**
> Ok, that's not good, the dmask value (0000) didn't hold on re-inserting the usb stick -- that is the problem continues the same.

The dmask value is the only thing I can see for blocking rw access.

I will continue looking around, but if anyone else has ideas for setting the dmask value on removable usb drives to 0000 permanently they would be worth looking into.
I was looking around as well about this issue, and in one thread I found, someone was saying that for all usb storage devices, Ubuntu has it preprogrammed into the system that if a device ends up having a problem of some kind, either while deleting or doing anything at all with it, the system will automatically change it to being written as read only, in order to protect the data inside or something. The guy said that this was built in in order to protect storage devices from things such as power outages and stuff.

Could this have something to do with it?

---

### Post by yetiman64 on 2010-11-16
Can you drop a link to that post / thread so I can have a look, even just copy/paste the address from your browser address bar to here without linking if you wish? It may very well apply.

---

### Post by Jotaro on 2010-11-16
> **yetiman64 said:**
> Can you drop a link to that post / thread so I can have a look, even just copy/paste the address from your browser address bar to here without linking if you wish? It may very well apply.
[http://ubuntuforums.org/showthread.php?t=456206](http://ubuntuforums.org/showthread.php?t=456206)

Kernel Tom says:
"It seems to do this after it goes into "sleep mode".  My guess is that  Ubuntu believes that something has happened to the device (like a power  failure or yanking out the usb chord) _and makes the drive read only_ to  protect data."

---

### Post by yetiman64 on 2010-11-16
> **Jotaro said:**
> [http://ubuntuforums.org/showthread.php?t=456206](http://ubuntuforums.org/showthread.php?t=456206)

Kernel Tom says:
"It seems to do this after it goes into "sleep mode".  My guess is that  Ubuntu believes that something has happened to the device (like a power  failure or yanking out the usb chord) _and makes the drive read only_ to  protect data."

Just noted they all seem to be talking about ext formatted drives not FAT, so probably doesn't apply here.

One more idea I've had is to manually mount the drive again this time specifying more mount options compared to last time. I'm getting the idea from [--here--.]("https://help.ubuntu.com/community/Mount/USB#Using%20mount")

Unmount the drive (but don't remove it) with,
```
sudo umount /media/"UDISK 2.0"
```Then in terminal use,
```
sudo mount -t vfat /dev/sdb1 ~/USB_disk -o uid=1000,gid=1000,utf8,dmask=0000,fmask=0111
```this should remove the dmask restriction, the fmask=0111 sets the files without an execute bit only. The dmask and fmask values are different to the link to suit your purposes here. You will be using the mountpoint in your home directory again this time.

Let us know if this gives read/write access, and if it does, see if you can complete the tasks you were attempting earlier creating/deleting files/folders and emptying the trash etc.

---

### Post by Jotaro on 2010-11-16
> **yetiman64 said:**
> Just noted they all seem to be talking about ext formatted drives not FAT, so probably doesn't apply here.

One more idea I've had is to manually mount the drive again this time specifying more mount options compared to last time. I'm getting the idea from [--here--.]("https://help.ubuntu.com/community/Mount/USB#Using%20mount")

Unmount the drive (but don't remove it) with,
```
sudo umount /media/"UDISK 2.0"
```Then in terminal use,
```
sudo mount -t vfat /dev/sdb1 ~/USB_disk -o uid=1000,gid=1000,utf8,dmask=0000,fmask=0111
```this should remove the dmask restriction, the fmask=0111 sets the files without an execute bit only. The dmask and fmask values are different to the link to suit your purposes here. You will be using the mountpoint in your home directory again this time.

Let us know if this gives read/write access, and if it does, see if you can complete the tasks you were attempting earlier creating/deleting files/folders and emptying the trash etc.

Did everything you said, and it is still giving me the exact same error on trying to permanently delete a file from the trash bin. Also, something I didn't mention before as I didn't think it was that important, when I click "Empty Trash" in order to try to empty all of the trash, nothing happens. There is no response at all, and the files do not get removed.

---

### Post by yetiman64 on 2010-11-16
OK I would suggest you unmount from the home folder (the command has been used here before), safely remove the drive (also done before) and reinsert as a standard mount.

I seem to have run into a brick wall here and am probably missing something in the processes. You may need to wait for someone more experienced with mounting of FAT partitions to help out here.

If you need to use the usb stick with Windows I suggest you consider NTFS formatting, as it is easier to handle using the ntfs-config package in Ubuntu than FAT drives. I use an 8GB usb stick here formatted to NTFS without problems this way.

Good luck and I'll keep an eye on how this works out.

---

### Post by zzart on 2011-01-10
> **Jotaro said:**
> Did everything you said, and it is still giving me the exact same error on trying to permanently delete a file from the trash bin. Also, something I didn't mention before as I didn't think it was that important, when I click "Empty Trash" in order to try to empty all of the trash, nothing happens. There is no response at all, and the files do not get removed.

Hi,
Maybe i ve missed something as i don't have time to read the entire thread but i had similar problem to urs (read-only mounts and Empty trash thing )
It happend as I used usb with Windows and and  didn't unmount it properly there (i my case i did just removed it as windows was shutting down) then plugging it to ubuntu i got these problems. Maybe it has sth to do with garbage left by M$ ? 
anyway to fix it i plugged it back to M$ station and did repair file structure , unmont it properly and i was back to normal with working on Ubuntu. 
good luck,

---

### Post by darkstaar on 2011-01-10
I've run into this problem with at least a half dozen separate USB sticks and I believe that I finally figured out the solution.

Stay away from off-brand media.

I've had about a dozen of those bargain USB sticks over the years and _every_ single one of them has failed within a few weeks of purchase. About half of these junk drives suddenly became read-only, as yours did. The rest crapped out completely.

On the other hand, all of my brand-name media sticks continue to perform perfectly (Kingston, Sandisk, etc.) including my old 512mb Verbatim which is at least eight years old and still in daily service.

---

