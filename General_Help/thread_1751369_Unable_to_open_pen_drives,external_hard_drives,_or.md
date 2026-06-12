---
title: "Unable to open pen drives,external hard drives, or mount other partitions"
date: 2011-05-06
forum: General Help
---

### Post by apoorvumang on 2011-05-06
I have been unable to open any pen drive or external hard drive as their icon does not show on the desktop or in the 'Computer' location.

lsusb shows that the pen drive is connected, fdisk -l also lists it.

However, I am unable to open them because of the absence of icons. Perhaps I can mount them through a terminal command? I'm a newbie to computers.

---

### Post by apoorvumang on 2011-05-07
bump

---

### Post by triceratops on 2011-05-07
Here are some suggestions that might help.

First, open a terminal and get into root.  This is done with the *su* command.  If you haven't already set a superuser password, then type

```
sudo passwd
```

Type in a password and then type

```
su
```

and enter your new superuser password.  If you see the # prompt, you are in root.

Next, what you might want to do is check the contents of your /media directory. Type (or cut n paste)

```
cd /media && ls -FAtrls
```

This will give you a list of the peripheral devices (pen drive, external HDD) that are currently mounted to yoursystem.  You may access the content of these mounted drives or partitions like the contents of any other folder.  In order to access these files, you will have to be root or use *sudo*, as the media folders are usually owned by root.

If you don't see your particular device in the /media directory, run again

```
fdisk -l
```

or see what's in your fstab file by typing

```
less /etc/fstab
```

and take note of the items mounted and what type of file format the device uses (fat32, ext, etc.)  Then type 

```
mount -t <type> <device> <directory>
``` 

I suggest mounting the drive in the /media directory, though it's your call.

**For example**, let's say I had a SATA drive partition located at /dev/sda4 that has been mounted using the ext4 file system.  If I wanted to access this as a directory in /media, I would type:

```
mount -t ext4 /dev/sda4 /media/sda4
```

and then go ahead and access the data like in any other file directory.

-------------------

In my experience, items that are not visibly mounted as icons will probably be mounted in /media anyway.  If you'd like, simple create a soft link from the /media directory to the desktop.  Retrieve files from devices or partitions mounted to /media from the softlink.

---

### Post by apoorvumang on 2011-05-08
Hi there triceratops.
I tried what you said, but sadly it didn't work for me.
Here are the outputs of some commands. I have attached a 4gb transcend pen drive that I am unable to open.

**Output of lsusb:**
```

Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c019 Logitech, Inc. Optical Tilt Wheel Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash Flash Drive
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

It shows the pen drive as "Bus 001 Device 003: ID 058f:6387 Alcor Micro Corp. Transcend JetFlash".

**Output of fdisk -l:**

```
root@desktop:/media# fdisk -l
omitting empty partition (5)

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00040397

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       18723   150389761    5  Extended
/dev/sda2           18237       18723     3905536   82  Linux swap / Solaris
/dev/sda3   *       20031       30402    83301376    7  HPFS/NTFS
/dev/sda5               1       17977   144397312   83  Linux
/dev/sda6           17977       18237     2081792   82  Linux swap / Solaris

Disk /dev/sdb: 4016 MB, 4016046080 bytes
255 heads, 63 sectors/track, 488 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         489     3921856    b  W95 FAT32
Partition 1 has different physical/logical endings:
     phys=(487, 254, 63) logical=(488, 65, 25)

```

/dev/sdb1 seems to me to be the pen drive.

**Output of ls -FAtrls:**

```

root@desktop:/media# ls -FAtrls
total 0

```

Here's where the problem starts. /media does not have the pen drive mounted.

So, do I need to mount the pen drive in some way?
The mount command isn't working for me. Here's the output:
```

root@desktop:/media# mount -t fat32 /dev/sdb1 /media/sdb1
mount: mount point /media/sdb1 does not exist
root@desktop:/media# mount -t fat32 /dev/sdb1 /media
mount: unknown filesystem type 'fat32'

```
I must be doing something wrong here.

Also, here's what less /etc/fstab shows:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sda6       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=6a018e4e-c6e3-4821-8382-b55b05700048 none            swap    sw              0       0
/etc/fstab (END) 

```

Is there something missing here?

---

### Post by apoorvumang on 2011-05-08
I installed a GUI program for mounting external drives called usermount. If run as 'sudo usermount', it shows the pen drive as:

File system: proc
Mount Point: /proc
Type: proc

This is the same as that in 'less /etc/fstab'.

If I run the program as normal user(without sudo), it doesn't show any external drive.

Why is this happening?

---

### Post by apoorvumang on 2011-05-08
Finally able to mount an external hard drive with the command
```

sudo mount -t ntfs /dev/sdb1 ~/HD

```

However, if I attempt to unmount it without being root, it says this:
```
umount: /home/apoorv/HD is not in the fstab (and you are not root)

```

Is there any way to restore things back to normal? Any hints as to what I should do?

---

### Post by apoorvumang on 2011-05-11
Bump.
Is anyone else having this problem? Could anyone guide me as to where I might find a solution for this?

---

### Post by jchw on 2011-05-14
I have exactly the same problem and have been working for a few days to resolve it without success. I opened a thread unable to see flash drive but had no responses that fixed the problem

I thought yesterday I had fixed it because I had blacklisted from drivers when I was trying to make the wifi card work. When I unblacklisted the drivers the USB appeared to work but I spoke too soon. The problem is back.

I find I can get into the USB memory stick by shutting down and starting up with the stick inserted. Although it comes up a a Pendrive in Places it seems to be usb0 acts like a hard drive.

Some people seem to be reporting this as a problem relating to the upgrade to 11.4 but I have not upgraded yet so it must be a general issue.

I suspect it is due to a routing update around last Monday or Tuesday but I cannot be certain.

Should  this be reported as a bug?

---

