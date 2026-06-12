---
title: "External hard drive mount issues"
date: 2011-08-22
forum: General Help
---

### Post by vivakh on 2011-08-22
Hi guys,

I have a problem accessing my external hard drive. In windows, it tells me to format the drive. in linux, i get "DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending" sometimes, but right now its mounted and can be accessed. but its very slow and the partition type is "fuseblk" when i checked it in the file systems tab of the system monitor.

sudo /sbin/fdisk -l
```

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x613d024b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
/dev/sda2              13       11762    94371840    7  HPFS/NTFS
/dev/sda3           11762       19453    61773824    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4256    34179072   83  Linux
/dev/sdb2            4256       19210   120116224   83  Linux
/dev/sdb3           19210       19453     1951744   82  Linux swap / Solaris

Disk /dev/sdd: 1000.2 GB, 1000170586112 bytes
255 heads, 63 sectors/track, 121597 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x6186009b

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1      121598   976728064    7  HPFS/NTFS
```

The drive sdd is the external hard drive. Its actually mounted twice right now, sdc and sdd. when i open sdc, i get no files in the folder, but when i open sdd, i see all my files.

I'd really like to get my drive back up and running properly, any help would be gladly appreciated.

Thanks in advance,
Vivakh.

---

### Post by vivakh on 2011-08-22
Anyone have an idea whats up here?

---

### Post by dandnsmith on 2011-08-22
Looks like you're set up to use the fuse.. stuff for handling NTFS.
A thought (from one who  hasn't faced this problem) that you might need to try the ntfs-3g package to handle it successfully.

---

### Post by vivakh on 2011-08-22
Thanks for your response. Where can i obtain that from?

I tried fixing this in windows as well, i dont know if im getting anywhere. There's a program called Test Disk that im using. It's used to recover partitions, and files from corrupted drives, deleted partitions etc. In this program, i can see my drive, access it and repair the file system. after i do that and restart, the drive still doesn't detect.

---

### Post by dandnsmith on 2011-08-22
Just looked at your reply, and am kicking myself for not noticing the implications of Windows not recognising it as formatted.
If you can see the files, then the thing is to copy them as quickly as possible (you've checked it isn't just the filenames you're seeing?).

Then you need to run a proper diagnostic, to see if the problem can be localised to the disk (the other usual culprit, tho' we've no evidence of that, is RAM)


The ntfs-3g comment was based on it only being Ubuntu not handling it correctly (should be available through the package manager/Synaptic).

---

### Post by vivakh on 2011-08-22
This problem started last night when i was transferring some files to the external drive and the power went out. When i rebooted, those were the messages i was getting. Windows tell me the drive needs to be formatted, ubuntu tells me DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending.

I installed test disk in linux and ran it. I repaired the ntfs partition, and can now access my drive, see all my files (700gb+) However, when browsing in the drive, i notice that the folders take a little while to respond. The light on my hard drive goes "blink blink blink '......blank......' blink blink blink" in that pattern all the time when i'm on the drive. Seems to me like it cant utilise the full speed of the drive. I guess its because it hasn't been fixed properly, because when i log back into windows, the drive shows up as local disk and the file system is raw.

How can i run a proper diagnostic on the drive as you mentioned? I take that you're suggesting that maybe the ram is bad?

Thanks for replying.
Vivakh.

---

### Post by dandnsmith on 2011-08-23
The HDD manufacturers often provide their own diagnostics, and there also some in the various recovery disks.

The mention of RAM problem is in case the disk diagnostic fails to find a problem, and you need somewhere else to try.

The blink blink blink suggests there is a problem reading, but that doesn't necessarily mean a disk hardware problem. As I said, concentrate on retrieving any desired files, and then tackle the HDD as a wipable option (so disk diagnostic can be really thorough).

---

### Post by vivakh on 2011-08-23
The western digital diagnstic tool ran ok, the drive is healthy.

Here's an update, guys...This drive now mounts, after a little waiting, < 5 mins, When it mounts, i see all my files, the speed however is very slow, sometimes file manager hangs when im trying to navigate to a file. When i do manage to select something to copy, i get transfer rates of 400 - 600 kbps. I don't mind waiting for700 gb of data to transfer at that speed as i need the data usable again, the problem is after a few minutes of copying, the drive will unmount itself. Does anyone have any idea how i can make this drive perform better and solve this random unmounting issue?

Test disk informs me that the boot sectors of the disk are ok, but when i try to check the MFT, i get this message, "Both MFT seems ok but they don't match, use chkdsk." 
So i guess maybe it has something to do with the MFT? How can i repair this?

---

### Post by dandnsmith on 2011-08-24
Sounds like you have a direct hint - get to Windows, and use chkdsk (in repair mode ie chkdsk /f)

---

### Post by vivakh on 2011-08-24
Tried that, chkdsk /f freezes after a while, then displays input/output error.. :(

---

### Post by westie457 on 2011-08-24
Hi just some suggestions for you to try.

Leave the hard drive connected and boot your copmuter into whichever OS you want either will do.

When everything has settled then safely remove the drive from the OS and unplug it. Turn off the computer, plug the drive in again and repeat the process for the other OS.

One of the operating systems has put a lock onto the hard drive. This was caused by the power failure while the drive was in use and the operation in use at the time did not have time to finish. The safe removal of the drive from the OS should now return things back to normal. 

It is still advisable to run Windows CHKDSK /f over the drive to be on the safe side.

---

### Post by vivakh on 2011-08-24
Hi, i actually tried doing this before i read this post, lol. I connected it to the pc, from off state, powered up, booted into windows, windows detected it, then powered down, booted into ubuntu, now my files are copying at 7 - 10 mbps, and the drive hasn't disconnected itself yet. So in a couple more hours, (200+ gb already saved), all my files will have been copied over.

Another question, after i have copied all my info off, should i still run test disk? or should i just do a clean format of the ntfs file system? If i do a clean format, will the boot sector and the MFT be repaired?

---

### Post by vivakh on 2011-08-25
> **vivakh said:**
> 
Another question, after i have copied all my info off, should i still run test disk? or should i just do a clean format of the ntfs file system? If i do a clean format, will the boot sector and the MFT be repaired?

Anyone?

---

### Post by vivakh on 2011-08-27
Any help guys? My disk is still not functioning as it should. All my data is saved, i just want my WD Passport to function as it used to before. My read and write speeds to it are slow as it is right now. Writing to it starts off at 20 mbps, then drops a few mb every second till it reaches 6 mbps and it drops lower depending on how long i leave it to transfer. Im no expert, but this doesn't seem like the way it should behave.

After a full format to the drive, test disk tells me boot sectors are fine, but "MFT and MFT mirror are bad. Failed to repair them."

How can I get this drive up and functioning again? Any suggestions are welcome.

Thanks.

---

