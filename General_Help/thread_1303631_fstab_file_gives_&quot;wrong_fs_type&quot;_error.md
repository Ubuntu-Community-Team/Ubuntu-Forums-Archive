---
title: "fstab file gives &quot;wrong fs type&quot; error"
date: 2009-10-28
forum: General Help
---

### Post by G1imt on 2009-10-28
As i mount my freshly formatted media harddrive, I'm not allowed to create files or directories in it, which SUCKS because i specified "rw" in the fstab mount options. I notice that the HDD is "owned" by root.

This is my fstab file
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
UUID=063f488f-4148-4674-9da5-57483882d730 /	ext3	relatime,errors=remount-ro 0       1
/dev/scd0       /media/cdrom0   udf	iso9660,user,noauto,exec,utf8			0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8			0       0
/dev/sdb1       /media/Storage  ext3    auto,rw,exec,user				0	0
```

sdb1 is a freshly formatted ext3 partition on a hdd with msdos partition table (I chose msdos because it was default)

I want my 350GB harddrive connected with all permissions in place and with it's correct label "System"

Anyone?

Thanks

---

### Post by jward3010 on 2009-10-28
A manual mount might be the best option to try first.
```
sudo mount -t ext3 /dev/sdb1 /media/Storage
```

Double check the output of "fdisk -l" (thats an L) to make sure you have device names correct, for example are you sure it's "/dev/sdb1"?

---

### Post by G1imt on 2009-10-28
I've updated my first post after editing the mount options

I tried your manual mount though, and it made no difference. I'm guessing it's because root is the owner - and I'm not him.

And I'm quite certain it's sdb1

> g1imt@g1imt-PC:~$ sudo fdisk -l

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d4fbd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       24027   192996846   83  Linux

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9f9e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       38913   312568641   83  Linux


However I don't understand why it's "System" is Linux, as i formatted it as ext3

---

### Post by jward3010 on 2009-10-28
You are when you put "sudo" in front of your command. If you want to become true root on the command line, not recommended consistently, type:
```
sudo su
```
and retry mount command. I don't recommend you stay in that mode of access, to leave type "exit".
Did the output of "fdisk -l" confirm to you it was /dev/sdb1?

---

### Post by jward3010 on 2009-10-28
> **G1imt said:**
> However I don't understand why it's "System" is Linux, as i formatted it as ext3
Thats what fdisk calls Linux based file systems - Linux, it's still ext3, don't worry.

---

### Post by coffeecat on 2009-10-28
> **G1imt said:**
> I'm guessing it's because root is the owner - and I'm not him.

Yes, that's the reason. You've run into a permissions problem. Your drive is being mounted by root and is readable/writeable only by root. But there's a way round this. Try this. Let the drive be mounted on /media/Storage, open a terminal, and:

```
sudo mkdir /media/Storage/myfiles
```Now you need to change the permissions of the myfiles directory to you, thusly:

```
sudo chown G1imt: /media/Storage/myfiles
```Change 'G1imt' to whatever your account username is in your system, and don't miss the colon ( : ) after your username. Now you'll be able to read and write, make folders, etc in the folder myfiles, but not in the root of the drive. Not completely elegant, but usable. Obviously, substitute whatever folder name that you like for 'myfiles'

There is a way of getting ownership of a mounted ext3 drive/partition to an ordinary user, but I've forgotten the exact syntax. Perhaps someone could help. It would probably involve UIDs and/or GIDs in the fstab line.

---

### Post by G1imt on 2009-10-28
That's not the problem. As long as i'm in the terminal in root mode, i can add and remove files as much as i want, but I'm talking outside the terminal. It wont let me move click&drag my files over, telling me i dont have the "privileges".

EDIT: Yeah, coffeecat has got it, that's my problem - i see you've also given me some terminal commands to run - lovely. I'll report back!

---

### Post by coffeecat on 2009-10-28
> **G1imt said:**
> That's not the problem. As long as i'm in the terminal in root mode, i can add and remove files as much as i want, but I'm talking outside the terminal. It wont let me move click&drag my files over, telling me i dont have the "privileges".


Mmmmm. I think you've misunderstood me. Create the folder and chown it with sudo or as root. Then you can use the gui as an ordinary user to drag and drop file into the 'myfiles' folder as much as you want.

---

### Post by G1imt on 2009-10-28
chown worked, and i'm now allowed to drag my music & movies over. However I'm not permitted to delete the useless lost+found folder or right click and "create file- or directory"

I do expect that the second problem will be fixed by a simple remount or computer reboot though.

---

### Post by G1imt on 2009-10-28
> **coffeecat said:**
> Mmmmm. I think you've misunderstood me. Create the folder and chown it with sudo or as root. Then you can use the gui as an ordinary user to drag and drop file into the 'myfiles' folder as much as you want.

I didn't missunderstand you :P I just posted at the same time you did :)

---

### Post by drs305 on 2009-10-28
> **G1imt said:**
> That's not the problem. As long as i'm in the terminal in root mode, i can add and remove files as much as i want, but I'm talking outside the terminal. It wont let me move click&drag my files over, telling me i dont have the "privileges".

EDIT: Yeah, coffeecat has got it, that's my problem - i see you've also given me some terminal commands to run - lovely. I'll report back!

Try this.
Unmount sdb1:
```

sudo umount /dev/sdb1

```

Open fstab for editing and make this the entry for sdb1:
```

/dev/sdb1  /media/Storage  ext3 defaults,users 0 2

```

Make yourself the owner of storage:
```

sudo chown -R g1imt: /media/Storage

```

Mount sdb1:
```

sudo mount -a

```
If you don't get any error messages, it mounted, you are the owner, and you can do what you want with the contents.

---

### Post by alphaniner on 2009-10-28
root can delete the lost+found folder, but you should leave it be.  It is created during formatting for a reason.

---

### Post by coffeecat on 2009-10-28
> **G1imt said:**
> I didn't missunderstand you :P I just posted at the same time you did :)

Excellent! Glad we're singing from the same hymn sheet! :wink:

By the way, I agree with **alphaniner**. Leave the Lost+Found folder; don't delete it.

And try **drs305**'s suggestion. That will be more elegant than mine.

---

### Post by G1imt on 2009-10-28
I got the thing working 60 seconds after u showed me the chown function, coffeecat ;)
Thanks for your help!

I did however wonder how to set the label to "Storage" as I'm not allowed to do this by renaming the icon in Computer.
I get this error
> Sorry, could not rename "320.1 GB Media" to "Storage": Operation not supported by backend

Thanks

---

### Post by drs305 on 2009-10-28
For an ext3 partition:
```

sudo tune2fs -L <label> <dev>

```
Example: 
sudo tune2fs -L Storage /dev/sdb1

Added: You can also label a partition in Gparted and, with Karmic, via System, Administration, Disk Utility

---

### Post by egalvan on 2009-10-28
> **G1imt said:**
> 

I did however wonder how to set the label to "Storage" as I'm not allowed to do this by renaming the icon in Computer.
I get this error


Thanks

I don't think you can change the label while the drive is mounted.
Try un-mounting first

And Linux is Not Windows, so changing the Icon label may not change the partition label.

There are ext2 tools to set a label on an ext3 partition.

Guru? do any of you remember what it is?

edit; ok drs305 got it,
thanks

---

### Post by G1imt on 2009-10-29
Yeah, this sets the label, i guess. But the label was already Storage, as i set it as such when i formatted. The mounted device is still called "320.1 GB Media" when mounted though.

---

### Post by G1imt on 2009-10-29
I checked the device's properties and got quite surprised. It doesn't know it's own mount point or options. Also it thinks it doesn't have a label. What have i done wrong?

---

