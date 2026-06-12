---
title: "Cannot mount volume"
date: 2009-07-18
forum: General Help
---

### Post by kklungre on 2009-07-18
My windows XP died so my flatmate gave me an Ubuntu 8.04 cd in order to backup my data.

When I try to access any of my HDDs I get the error message "Cannot mount volume"

""$Logfile indicates unclean shutdown (0, 0) Failed to mount '/dev'sda5': Operation not suppoerted Mount is denied because NTFS is marked to be in use. Choose one action: Choice 1: If you have Windows then disconnect the external devices by clinking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2: If you don't have Windows then you can use the 'force' option for your own responsibility. for example type on the command line: mount -t ntfs -3g /dev/sda5 /media/disk -o force""

I've tried to use the command line but unfortunately I'm a noob when it comes to Linux and I haven't been able to find any help by googling.

Any help will be appreciated.

---

### Post by merlinus on 2009-07-18
Open a terminal, type in this command, and post results

```
sudo fdisk -l
```

---

### Post by pbpersson on 2009-07-18
What error message do you get when you attempt the:

mount -t ntfs -3g /dev/sda5 /media/disk -o force

command from the terminal prompt?  Do you need to put "sudo" in front of that command to make it work?

---

### Post by kklungre on 2009-07-18
> **merlinus said:**
> Open a terminal, type in this command, and post results

```
sudo fdisk -l
```

Result:

"fdisk: invalid option -- 1"

---

### Post by kklungre on 2009-07-18
> **pbpersson said:**
> What error message do you get when you attempt the:

mount -t ntfs -3g /dev/sda5 /media/disk -o force

command from the terminal prompt?  Do you need to put "sudo" in front of that command to make it work?

mount -t ntfs -3g /dev/sda5 /media/disk -o force

---> result: invalid option -- 3

sudo mount -t ntfs -3g /dev/sda5 /media/disk -o force

----> result: invalid option -- 3 + I get a longer list of different commands

---

### Post by merlinus on 2009-07-18
l is a lowercase L, not the number 1.

Also, no space:  ntfs-3g

---

### Post by Sidewinder1 on 2009-07-18
You made a slight mistake; it's fdisk -l (as in the letter lower case l, not 1 (number 1))
I found, as a result of making that exact same mistake, that it's better to copy and paste the commands into your terminal rather than typing. The fact that I'm a "peck and hunt" man has *absolutely* nothing to do with it, thank you all very much...

HTH,
 Side

---

### Post by Gizenshya on 2009-07-18
there is no space between "ntfs" and "-3g"

that section should be "ntfs-3g"

---

### Post by Sidewinder1 on 2009-07-18
That proves my point... :-(

---

### Post by kklungre on 2009-07-18
> **merlinus said:**
> l is a lowercase L, not the number 1.

Hehehe, sorry about that.

Results:

"Disk /dev/sda: 320.0 GB
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x188d188d

  Device    Boot     Start      End     Blocks         Id   System
/dev/sda1 *                1     2550   20482843+    7   HPFS/NTFS
/dev/sda2              2551    38912  292077765    f    W95 Ext'd (LBA)
/dev/sda3              2551    38912  292077733+  7   HPFS/NTFS


Disk /dev/sdb: 250.0 GB
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

Device      Boot    Start   End      Blocks        Id  System
/dev/sdb1       *         1   30401  244196001  7   HPFS/NTFS

Disk /dev/sdc: 120.0 GB
 255 heads, 63 sectors/track, 14596 cylinders
 Units = cylinders of 16065 * 512 = 8225280 bytes
 Disk identifier: 0x39337a2e

Device      Boot    Start   End      Blocks        Id  System
/dev/sdc1                 1   14595  117234306  7   HPFS/NTFS"

---

### Post by kklungre on 2009-07-18
> **Sidewinder1 said:**
> You made a slight mistake; it's fdisk -l (as in the letter lower case l, not 1 (number 1))
I found, as a result of making that exact same mistake, that it's better to copy and paste the commands into your terminal rather than typing. The fact that I'm a "peck and hunt" man has *absolutely* nothing to do with it, thank you all very much...

HTH,
 Side

I haven't got an internet connection on my pc, I'm typing on my laptop now.

Copy and paste is not an option unfortunately.

---

### Post by kklungre on 2009-07-18
> **pbpersson said:**
> What error message do you get when you attempt the:

mount -t ntfs -3g /dev/sda5 /media/disk -o force

command from the terminal prompt?  Do you need to put "sudo" in front of that command to make it work?

Result:

"$LogFile indicates unclean shutdown (0, 0)
WARNING: forced mount, reset §LogFile
fuse: failed to access mountpoint /media/disk: No such file or directory"

---

### Post by kklungre on 2009-07-18
If there are any other ways for me to copy files from my disks to an external drive feel free to educate my poor little mind.

---

### Post by merlinus on 2009-07-18
If you did not do so, you need to first create a mountpoint.

```
sudo mkdir /media/disk
```Then you can try to mount the partition:

```
sudo mount -t ntfs-3g /dev/sda5 /media/disk -o force
```

---

### Post by michy99 on 2009-07-18
You need to create a mountpoint before you can mount.```
sudo mkdir /media/disk
sudo mount -t ntfs-3g /dev/sda5 /media/disk -o force
```

Too slow again!

---

### Post by kklungre on 2009-07-18
> **merlinus said:**
> If you did not do so, you need to first create a mountpoint.

```
sudo mkdir /media/disk
```Then you can try to mount the partition:

```
sudo mount -t ntfs-3g /dev/sda5 /media/disk -o force
```

Didn't work.

"fuse: mount failed: Device or resource busy"

---

### Post by merlinus on 2009-07-18
Try this:

```
sudo umount /dev/sda5
sudo mount -t ntfs-3g /dev/sda5 /media/disk -o force
```

---

### Post by kklungre on 2009-07-18
Haha, suddenly I found my main disk on the desktop. Wohoo!

Now what do I do to open the other disk and the external drive I've got plugged in my USB port? :D

---

### Post by kklungre on 2009-07-18
Everything worked out in the end. Thanks for the help guys!

---

