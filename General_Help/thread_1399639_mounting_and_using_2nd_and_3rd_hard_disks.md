---
title: "mounting and using 2nd and 3rd hard disks"
date: 2010-02-05
forum: General Help
---

### Post by DanBender on 2010-02-05
I'm trying to set up an installation of Mythbuntu on an older computer and am having some issues with setting up a second and third hard drive to handle my media.

I have a 40 GB drive which is my primary; I installed Mythbuntu to it and then *moved it into the current machine.* It was installed on an XFS partition.

I have a 160 GB drive I wish to use to store photos and home movies. This will be shared over my home network using samba. I downloaded Palimpest Disk Utility using Synaptic and used it to put an ext4 filesystem on it. It appears to have been made successfully in the disk utility, but I'm not sure if it's mounted. The filesystem is called "media-disk"

I have a 1 TB drive that I'm going to use as the MythTV tv-show disk. I believe I saw in the the Mythbuntu documentation something about XFS (plus, that's what the main is installed to), so I attempted to create an xfs filesystem called "tv-disk" on it using the disk utility, but it returned the following error (it also errored when I tried to create media-disk as xfs):

Error creating partition
The operation failed.
Details:
```
Error creating file system: helper exited with exit code 1: cannot spawn 'mkfs.xfs -L "tv_disk" /dev/sdc': Failed to execute child process "mkfs.xfs" (no such file or directory)
```So I'm not really sure where I'm at here. My questions are:

1) which filesystem should I be using if I'm going to share using Samba? Is ext4 okay?
2) which filesystem should I be using for MythTV recordings?
3) if the answer to 2) is "xfs", how do I do that?
4) once I have the correct filesystems created, how do I mount them for what I need?

I know of the [FONT=Courier New]mount[/FONT] command, but I'm unsure of the correct syntax. I tried:
```
mount -t ext4 media-disk media
```to mount the media-disk filesystem I successfully created, but it didn't work. I'm not certain which parameters I got wrong.

I'm going to need to have those drives auto-mount when I log in, so I'm not even sure mount is the correct tool.

Thanks in advance for your help; I can stumble around with some basic stuff okay, but I'm new to the system-administration aspect of this.

-Dan

---

### Post by Barriehie on 2010-02-05
Post the output of:
```

sudo fdisk -l

```
that's a lower case L

Barrie

---

### Post by DanBender on 2010-02-06
Okay, I realized I needed to install xfstools from Synaptic, so the disk formatter worked at least semi-correct.

> **Barriehie said:**
> Post the output of:
```

sudo fdisk -l

```...
in the output below, /dev/sda# is the primary disk, /dev/sdb# is to be "media-disk," and /dev/sdc is to be "tv-disk."

And I messed up with my earlier descriptions - primary disk is ext4, not XFS.

```

Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc86b1d81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4794    38507773+  83  Linux
/dev/sda2            4795        5005     1694857+   5  Extended
/dev/sda5            4795        5005     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ebc9d80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
```

---

### Post by Barriehie on 2010-02-06
> **DanBender said:**
> ...muted...
in the output below, /dev/sda# is the primary disk, /dev/sdb# is to be "media-disk," and /dev/sdc is to be "tv-disk."
```

Disk /dev/sda: 41.2 GB, 41174138880 bytes
255 heads, 63 sectors/track, 5005 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc86b1d81

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4794    38507773+  83  Linux
/dev/sda2            4795        5005     1694857+   5  Extended
/dev/sda5            4795        5005     1694826   82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1ebc9d80

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       19457   156288321   83  Linux

Disk /dev/sdc: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

Disk /dev/sdc doesn't contain a valid partition table
```

Okay, from the terminal; Applications > Accessories > Terminal:
**Step 1 - Create a mount point for the photos/movies drive.**
```

cd /media
sudo mkdir ./mymedia
```

**Step 2 - Create a mount point for the Myth-TV drive.**
```

sudo mkdir ./mythtv
```

**Step 3 - Edit [b][color="green"]/etc/fstab[/color]** to automount above drives.  You'll be prompted for root password at this step and the editor will launch.[/B]
```

gksudo gedit /etc/fstab

```

**Step 4 - Copy/Paste the lines below to the end of your fstab file.**
```

#
# My photos/movies drive.
#
/dev/sdb1  /media/mymedia  auto  auto,user,exec,rw  0  2

#
# My myth-tv drive.
#
/dev/sdc1  /mythtv  auto  auto,user,exec,rw  0  2

```

**Step 5 - Save the file (letters can be lowercase)**
```

CTRL - S

```

**Step 6 - Close the file**
```

CTRL - W

```

**Step 7 - Quit the editor**
```

CTRL - Q

```

**Step 8 - Mount the drives from the CLI, sanity/typo check!**
```

mount -a

```

Shouldn't be any errors displayed and when you run Nautilus at this point the drives should show up in the side pane.  ([COLOR="Red"]If there are and they don't then you're back here. 8) [/COLOR])

**Step 9 - Close the terminal**
```

exit

```

Now, restart your machine and you should be set.  I don't know of any pros/cons of one fs over another for any time of media differences or what's involved using samba.  The above should have them automounted at boot time and a fscheck will be run I believe every 20 boots, this is adjustable via tune2fs.

HTH,
Barrie

---

### Post by DanBender on 2010-02-06
Thanks, Barrie! That looks like it did it. Well, not *exactly,* but I figured it out from what you suggested. Turns out sdc1 didn't exist, but when I edited it to just sdc, it appears to have mounted just fine. Maybe XFS drives don't mess around with that partition stuff and just exist as one big partition.

Again, thanks!

-Dan

---

### Post by Barriehie on 2010-02-06
> **DanBender said:**
> Thanks, Barrie! That looks like it did it. Well, not *exactly,* but I figured it out from what you suggested. Turns out sdc1 didn't exist, but when I edited it to just sdc, it appears to have mounted just fine. Maybe XFS drives don't mess around with that partition stuff and just exist as one big partition.

Again, thanks!

-Dan

Glad to help! 8)

---

