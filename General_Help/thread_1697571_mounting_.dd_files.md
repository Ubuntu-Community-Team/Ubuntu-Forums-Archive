---
title: "mounting .dd files"
date: 2011-03-01
forum: General Help
---

### Post by m91-30 on 2011-03-01
I have a .dd file from testdisk on an external hard drive. how do I mount this image to read it?

---

### Post by anglican on 2011-03-01
> **m91-30 said:**
> I have a .dd file from testdisk on an external hard drive. how do I mount this image to read it?The answer depends on whether you've imaged a partition or the entire device. If it's a partition then something like:
```
sudo mount -o loop -t auto /home/yourname/drive_image.dd /mnt/disk_image 
```should be what you need. You need to create /mnt/disk_image first with:```
sudo mkdir /mnt/disk_image
``` If it's an image of the entire device then take a look at this:

[http://ubuntuforums.org/showthread.php?t=711773](http://ubuntuforums.org/showthread.php?t=711773)

H

---

### Post by m91-30 on 2011-03-01
okay, first I entered:

udo mkdir /mnt/disk_image
then I entered:

sudo mount -o loop -t auto /media/My Passport/drive_image.dd /mnt/disk_image

as my image is on an external

then I get:

Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
One can change the type of mount containing the directory dir:
       mount --make-shared dir
       mount --make-slave dir
       mount --make-private dir
       mount --make-unbindable dir
One can change the type of all the mounts in a mount subtree
containing the directory dir:
       mount --make-rshared dir
       mount --make-rslave dir
       mount --make-rprivate dir
       mount --make-runbindable dir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .

---

### Post by anglican on 2011-03-01
> **m91-30 said:**
> 
sudo mount -o loop -t auto /media/My Passport/drive_image.dd /mnt/disk_image

It's the space between My and Passport. You need to escape it with a \ before the space:

```
sudo mount -o loop -t auto /media/My\ Passport/drive_image.dd /mnt/disk_image

```

H

---

### Post by m91-30 on 2011-03-01
okay, I typed:

sudo mount -o loop -t auto /media/My\ Passport/image.dd /mnt/disk_image

and got:

sudo mount -o loop -t auto /media/My\ Passport/image.dd /mnt/disk_image

I'm not quite sure how to do this. the image is of and on an ntfs drive, if that matters.

---

### Post by anglican on 2011-03-01
> **m91-30 said:**
> okay, I typed:

sudo mount -o loop -t auto /media/My\ Passport/image.dd /mnt/disk_image

and got:

sudo mount -o loop -t auto /media/My\ Passport/image.dd /mnt/disk_image

I'm not quite sure how to do this. the image is of and on an ntfs drive, if that matters.The "-t auto" should deal with what type of disk the image is of and it should't matter what sort of disk it's on. I don't quite follow what you mean in the above. Are you saying that you typed the command,pressed [ENTER] and nothing happened you just got your normal prompt back? If so it means that the mount has worked and the disk image is available to use. Try:
```
ls -l /mnt/disk_image

```to see what is on it. If you wanted an icon for the image on your desktop, change "mnt" to "media" and you'll get one. Otherwise just use whichever file manager program you normally use to look at the contents of the disk image.

H

---

### Post by m91-30 on 2011-03-01
I'm sorry, it didn't paste in right.

I type the command, then immediately after I hit enter, it gives me the prompt saying I need to specify the file system type. 

like this:

mount: you must specify the filesystem type

---

### Post by anglican on 2011-03-01
> **m91-30 said:**
> I'm sorry, it didn't paste in right.

I type the command, then immediately after I hit enter, it gives me the prompt saying I need to specify the file system type. 

like this:

mount: you must specify the filesystem typeAh, that's clearer. You could try "-t ntfs" but I suspect you may have the image of a whole device rather than a single partition. Take a look at the link I included in my first reply.

H

---

### Post by m91-30 on 2011-03-01
****. I think it isn't going to let me do this. I couldn't write the complete drive, as I only have a 500GB external. I really hope I don't need to go out and buy a 1TB external to do this.

I tried adding -t ntfs instead of auto, and got:

Failed to read last sector (1372762772): Invalid argument
HINTS: Either the volume is a RAID/LDM but it wasn't setup yet,
   or it was not setup correctly (e.g. by not using mdadm --build ...),
   or a wrong device is tried to be mounted,
   or the partition table is corrupt (partition is smaller than NTFS),
   or the NTFS boot sector is corrupt (NTFS size is not valid).
Failed to mount '/dev/loop0': Invalid argument
The device '/dev/loop0' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

also, I tried the link's suggested code as:

sudo mount -o loop,offset=32901120 -t auto /mnt/storage/disk_image /media/My\ Passport/image

and got:

/mnt/storage/disk_image: No such file or directory

I think I adapted it right, but can you please confirm?

I think my problem is, I imaged just a partition, as I meant to, but because it's technically an "incomplete" image, it won't let me do this.

---

### Post by anglican on 2011-03-02
> **m91-30 said:**
> 
also, I tried the link's suggested code as:

sudo mount -o loop,offset=32901120 -t auto /mnt/storage/disk_image /media/My\ Passport/image

and got:

/mnt/storage/disk_image: No such file or directory

I think I adapted it right, but can you please confirm?

I think my problem is, I imaged just a partition, as I meant to, but because it's technically an "incomplete" image, it won't let me do this.You need to do:

fdisk -u -l /media/My\ Passport/drive_image.dd

which should show an out put similar to:

> You must set cylinders.
You can do this from the extra functions menu.

Disk /mnt/storage/disk_image: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x41172ba5

                  Device Boot      Start         End      Blocks   Id  System
/mnt/storage/disk_image1              63       64259       32098+  de  Dell Utility
/mnt/storage/disk_image2   *       64260    78108029    39021885    7  HPFS/NTFS
Partition 2 has different physical/logical endings:
     phys=(1023, 254, 63) logical=(4861, 254, 63)_Your numbers will be different - you must use the numbers from your output_
Take the Start value of the partition you want to mount and multiply it by 512 in this example that would give you 32901120 then you type:
```
sudo mount -o loop,offset=32901120 -t auto /media/My\ Passport/drive_image.dd /mnt/disk_image
```to mount the image at /mnt/disk_image (in the version you used you would have needed to first create a directory called /mnt/storage and then a directory /mnt/storage/disk_image before running the mount command).

H

---

### Post by anglican on 2011-03-02
> **m91-30 said:**
> 
I think my problem is, I imaged just a partition, as I meant to, but because it's technically an "incomplete" image, it won't let me do this.If you can get it mounted, ntfsfix (in the ntfsprogs package) may help to correct any problems with the image. You can run it on the mounted image provided it is mounted read-only (add "-o ro" to the mount command). The command is:
```
sudo ntfsfix /dev/loop0

```H

---

### Post by m91-30 on 2011-03-02
okay, maybe I'm missing something, but I got:

You must set cylinders.
You can do this from the extra functions menu.

Disk /media/drive/image.dd: 0 MB, 0 bytes
255 heads, 63 sectors/track, 0 cylinders, total 0 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                Device Boot      Start         End      Blocks   Id  System


what number from this am I supposed to use?

---

### Post by m91-30 on 2011-03-02
also, I have since gone out and bought a big enough drive. and re imaged the 750GB drive.

---

### Post by m91-30 on 2011-03-02
I'm sorry if this seems like a dumb question, but this is my first time REALLY using terminal, and I do really appreciate the help. it's also my first time dipping into the world of advanced computing, beyond being able to use and alter linux and rooting/flashing android.

---

### Post by anglican on 2011-03-02
> **m91-30 said:**
> I'm sorry if this seems like a dumb question, but this is my first time REALLY using terminal, and I do really appreciate the help. it's also my first time dipping into the world of advanced computing, beyond being able to use and alter linux and rooting/flashing android.It looks like the image you were trying to mount contained no partition information i.e. it was (as you thought) the image of a partition and not a device (it would help if you described exactly how you made it). With a large enough external drive hopefully you will now be able to mount the image which presumably wouldn't mount before because it was incomplete.

H

---

### Post by m91-30 on 2011-03-02
I created it by going into testdisk and using "image creation" ([http://s620.photobucket.com/albums/tt283/adamlesandrini/?action=view&current=Screenshot.png](http://s620.photobucket.com/albums/tt283/adamlesandrini/?action=view&current=Screenshot.png)). it still doesn't want to mount. I have a 750GB image on a 1.5TB drive, so space isn't an issue.


I still get:

mount: you must specify the filesystem type

if I use auto, and:

ntfs_mst_post_read_fixup: magic: 0x9e1aa116  size: 1024  usa_ofs: 11552  usa_count: 21837: Invalid argument
Record 0 has no FILE magic (0x9e1aa116)
Failed to load $MFT: Input/output error
Failed to mount '/dev/loop0': Input/output error
NTFS is either inconsistent, or there is a hardware fault, or it's a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows twice. The usage of the /f parameter is very
important! If the device is a SoftRAID/FakeRAID then first activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for more details.

using ntfs.

---

### Post by m91-30 on 2011-03-03
now, when I fixed the partition, I only assigned a partition type, I didn't reformat it. could this be the issue? do I perhaps need to assign a file system to the drive or image? the partition does show up as ntfs, though, as you can see in the picture.

---

### Post by JKyleOKC on 2011-03-03
To anglican: I don't want to hijack this thread, but I have a similar problem at [http://ubuntuforums.org/showthread.php?t=1696673](http://ubuntuforums.org/showthread.php?t=1696673) and perhaps we can work together to get a handle on both situations. Would you take a look, please?

---

