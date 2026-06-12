---
title: "MP3 player suddenly read only"
date: 2009-12-20
forum: General Help
---

### Post by Berduchwal on 2009-12-20
I have following MP3 player:

lsusb
```
Bus 004 Device 003: ID 0402:5667 ALi Corp. Music player
```

and after using it for while one day it show me that I can not delete or copy any file to it as it was mounted read only.

I can still access the files and open them. The mp3 that are on the player I can still play them.

I started investigating.

Tried: gparted > check
```
Unable to open /dev/sdf read-write (Read-only file system).  /dev/sdf has been opened read-only.
The FATs don't match.  If you don't know what this means, then select cancel, run scandisk on the file system, and then come back.
```

Tried dmesg
```
[ 4958.830666] usb-storage: device found at 3
[ 4958.830670] usb-storage: waiting for device to settle before scanning
[ 4963.832281] usb-storage: device scan complete
[ 4963.835242] scsi 7:0:0:0: Direct-Access     USB 2.0  Storage Device        PQ: 0 ANSI: 0 CCS
[ 4963.835851] sd 7:0:0:0: Attached scsi generic sg6 type 0
[ 4963.845273] sd 7:0:0:0: [sdf] 4032512 512-byte logical blocks: (2.06 GB/1.92 GiB)
**[ 4963.848261] sd 7:0:0:0: [sdf] Write Protect is on**
[ 4963.848268] sd 7:0:0:0: [sdf] Mode Sense: 3b 00 80 00
[ 4963.848272] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 4963.863221] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 4963.863232]  sdf: sdf1
[ 4963.877250] sd 7:0:0:0: [sdf] Assuming drive cache: write through
[ 4963.877262] sd 7:0:0:0: [sdf] Attached SCSI removable disk

```

The mp3 player has no option of enabling write protection. While some players have hardware switch this one does not have one. Manual for the mp3 player does not mention such option as well.

fsck
```
marcin@marcin-desktop:~$ fsck /dev/sdf
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Permission denied while trying to open /dev/sdf
You must have r/w access to the filesystem or be root
marcin@marcin-desktop:~$ sudo fsck /dev/sdf
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Read-only file system while trying to open /dev/sdf
Disk write-protected; use the -n option to do a read-only
check of the device.



marcin@marcin-desktop:~$ sudo fsck /dev/sdf -n
fsck from util-linux-ng 2.16
e2fsck 1.41.9 (22-Aug-2009)
fsck.ext2: Superblock invalid, trying backup blocks...
fsck.ext2: Bad magic number in super-block while trying to open /dev/sdf

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device&gt;




marcin@marcin-desktop:~$ sudo dosfsck /dev/sdf
dosfsck 3.0.3, 18 May 2009, FAT32, LFN
Logical sector size (7950 bytes) is not a multiple of the physical sector size.

```

Tried to format in gparted but
```
Unable to open /dev/sdf read-write (Read-only file system).  /dev/sdf has been opened read-only.
Can't write to /dev/sdf, because it is opened read-only.
```

Can you please suggest some further steps to get it working.

---

### Post by hugmenot on 2009-12-20
Can the player format itself?

---

### Post by dcstar on 2009-12-20
These things die, try it on another PC and if it still does not work correctly then it is faulty.

---

### Post by DJ . on 2009-12-20
Right click the .mp3 file and a menu will pop up, click permissions, and for everything that says read only change to read and write.

---

### Post by Berduchwal on 2009-12-20
Mp3 player is fairly new about 3 months old.
It is very striped down version to make is very light and staff as it is water proof - so no self format available.
I can not changed permission it says that it is read only file system.

I tried on another instance of Ubuntu 9.04 today but effect was the same read only file system.

I will try in on Windows now.

----
On Windows I can edit, remove files, edit files.

---

### Post by hugmenot on 2009-12-20
Then format it from Windows. 

The message you earlier with the differing FATs hints at a file system corruption.

---

### Post by jmate24 on 2009-12-20
i have had the same problem with my gpx player and i found that if i opened the terminal and did this:

```
sudo nautilus /media/sdf
```

then i right clicked the empty white space and chose properties then went to permissions then changed the group owner to myusername and changed the folder permissions to r/w/x and then i closed the properties window then closed the open /media/sdf window and unmounted the media player and unplugged it then plugged it back in i could use it.

plus i would recommend that you format the drive and use fat32 instead of fat16.

jmate24--:)

---

### Post by Berduchwal on 2009-12-27
I tried to format the mp3 player using my printer... Samsung SCX 4828FN, but as a result MP3 stopped working.

Now Ubuntu not Windows detect it, it does not play either.

Will see how the producer responds to this.

---

### Post by ubunoob69 on 2011-10-27
identify the mount point of the device (usually /media/name_device) and type:
[SIZE=2]
$ sudo mount -o remount,rw /media/name_device[/SIZE]

that should re-mount the device with read-write access.

---

### Post by applejuicekiss on 2011-11-10
thanks ubonoob69.  your solution worked.  

it's been months since i plugged this thing in, and i have had to remount it rw in the past, but i couldn't remember what was needed.

---

