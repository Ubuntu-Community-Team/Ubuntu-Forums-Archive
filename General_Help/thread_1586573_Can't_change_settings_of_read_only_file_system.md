---
title: "Can't change settings of read only file system"
date: 2010-10-02
forum: General Help
---

### Post by nafihsus on 2010-10-02
:confused: 
When trying to copy files from a local folder into a directory that is a mapping of my QNAP server I get an error message "... Read-only file system" - and this only since a couple of days.

Trying to change ownership with sudo chown ... also failed with 

cenk@cenk-laptop:/mnt$ sudo chown cenk:cenk nas-video
chown: changing ownership of `nas-video': Read-only file system

The directory currently is owned by root/root but has 777 access rights. 
drwxrwxrwx 1541 nobody nogroup 86016 2010-08-21 07:36 nas-music
drwxrwxrwx   73 nobody nogroup  4096 2010-09-25 14:08 nas-pictures
drwxrwxrwx    8 root   root    12288 2010-09-13 23:27 nas-video

Here is the fstab line mapping the directory:
eldenas:/music  /mnt/nas-music  nfs
eldenas:/video  /mnt/nas-video  nfs

eldenas is my QNAP server.

No issues with the music directory but with the video one:

---

### Post by luvshines on 2010-10-02
You may need to check the export permissions from the server.

Can you paste the /etc/exports file from server.

Also, noticed that 2 of the directories are being owned by nobody/nogroup and one by root

Can you also paste the owner for those on server

---

### Post by SeijiSensei on 2010-10-02
It's likely that the filesystem has errors and was mounted read-only by the operating system.  That's what usually results in a "read-only file system" error. 

You'll need to unmount it and run something like 'fsck /dev/sda1' to fix the errors.  Then try mounting it again and see if it's still read-only.

You can force the system to remount the filesystem in read-write mode by using the command:

sudo mount -n -o remount,rw /dev/sda1 /mnt/point

but that's a last-ditch effort.  First find out why the OS was only willing to mount the filesystem read-only.  Browsing through /var/log/syslog and /var/log/messages might help, too.

If the device is an external drive of some sort, chances are it wasn't unmounted properly some time in the past.  If you must disconnect the external drive from some reason, umount the filesystems on it first.  You should also use "safely remove" if it's a USB device.  Some filesystems are more fragile than others on external drives.  I have one that I had formatted with XFS; it fell over if I looked at it funny.  I never had that problem with XFS on drives mounted in a computer, but it was too fragile a filesystem to use on a device which could be accidentally disconnected or powered off.  I reformatted it to ext4, and it's been much more robust.

---

### Post by nafihsus on 2010-10-03
The devices are directories on an external server (QNAP TS410) in my network. I can't find an /etc/exports file. Mounting works fine as I can read all files.

I don't know how the ownerships get mixed up as I always write from the same ubuntu client logged in under the same uid. 

Once unmounted to which drive should I apply the fsck command?

---

### Post by stillnotcool on 2010-10-03
I just experienced the same problem this morning, and this thread was very helpful for sorting out my problem.  Here's my scenario:

I store all my media (DVD backups, music files, and more) on an external hard disk, formatted HFS+ (non-journaled) so it interoperates with my wife's Mac and with the Western Digital Media Center connected to our TV.  Today I mis-read the cues of the WD Media Center and unplugged my external drive prematurely.  Not good.  No media was playing at the time, but the drive was not ready to be disconnected.

As soon as I reconnected the drive to my Ubuntu machine, it mounted read-only.  So I searched, found this thread, and made some progress with Ubuntu's built-in Disk Utility.  First, I unmounted the drive.  Then I used Disk Utility's built-in filesystem repair function to bring the drive back to life.  The filesystem appears to be fixed and the external drive is accessible again.

I do have one more question: How can I be sure that my data is safe (i.e., no corrupt)?  I've read that a damaged HFS+ filesystem can harm the data on a disk.  This hard drive contains literally thousands of files and represents years of collecting (not to mention quite a bit of money!), and I don't want anything to be wrong with the files.  How can I be sure none of the data is damaged?

Thanks in advance for your help.

---

### Post by nafihsus on 2010-10-09
Could you please explain in little more detail what exactly you did with the disk-utility.
The external drive doesn't appear in the list of drives when I start the utility.

---

### Post by dcstar on 2010-10-09
> **SemioticRobotic said:**
> 
I store all my media (DVD backups, music files, and more) on an external hard disk, formatted HFS+ (**non-journaled**) so it interoperates with my wife's Mac and with the Western Digital Media Center connected to our TV. 
.........
I do have one more question: How can I be sure that my data is safe (i.e., no corrupt)?  I've read that a damaged HFS+ filesystem can harm the data on a disk.  This hard drive contains literally thousands of files and represents years of collecting (not to mention quite a bit of money!), and I don't want anything to be wrong with the files.  How can I be sure none of the data is damaged?


[LIST=1]
[*]Please do not hijack threads, start an new thread with your issue.
[*]Journaling is specifically there to reduce chances of data corruption.
[/LIST]

---

### Post by stillnotcool on 2010-10-09
> **dcstar said:**
> [LIST=1]
[*]Please do not hijack threads, start an new thread with your issue.
[*]Journaling is specifically there to reduce chances of data corruption.
[/LIST]

[LIST=1]
[*]I felt that my problem was relevant to the topic at hand and that others with this problem could benefit from hearing a solution to it.
[*]Linux does not support both reading and writing to journaled HFS+ filesystems; thus, the choice was necessary.
[/LIST]

---

### Post by stillnotcool on 2010-10-09
> **nafihsus said:**
> Could you please explain in little more detail what exactly you did with the disk-utility.
The external drive doesn't appear in the list of drives when I start the utility.

I can try.

When I popped my external drive into the USB port, Ubuntu was able to mount it, but only as a read-only drive.  It appeared on my desktop, but I couldn't move any files TO it (though I could do a quick GRsync simulation to check the integrity of my data).  In Disk Utility, I could find the drive listed in the left panel, so I selected it and unmounted it.  After doing that, I was able to run the built-in filesystem check, which seemed to get me back up and running.

I have since reformatted the drive and restored my files from a backup, just to be safe.

---

### Post by nafihsus on 2010-10-23
I tried applying the brute force method recommended by SeijiSensei and remounted the drive with "rw" option.Even though the mount command didn't return an error, trying to change ownership still resulted in 'read only file system'.

---

### Post by SeijiSensei on 2010-10-23
> **nafihsus said:**
> I tried applying the brute force method recommended by SeijiSensei and remounted the drive with "rw" option.Even though the mount command didn't return an error, trying to change ownership still resulted in 'read only file system'.

The drive must still have filesystem errors then.  What kind of filesystem is it?  ext3/4? NTFS? FAT32? Something more arcane like XFS or JFS?  You need to run a native filesystem checker and get the drive sorted out.   If it's an NTFS or FAT32 drive, and you have a spare machine with Windows installed, try connecting the drive to that and running its disk repair utility if you can't seem to make headway with Linux.  Many other filesystems can be repaired with the Linux fsck utility, though a few, like XFS, have their own tools.

---

### Post by nafihsus on 2010-10-23
My NAS is a QNAP server TS410 formated as one volume in ext3 (RAID-5).
I am mounting various sub directories of the volume to music, video etc.
The video one is the only one making trouble.
I am already thinking of creating a new directory and copying all files to it and then deleting the old directory. But this is really last resort.

---

### Post by SeijiSensei on 2010-10-23
"Mounting" is a process applied to whole filesystems, not directories within them.  If you have one single filesystem with directories called /music and /video, you mount the whole filesystem just once and use /mntpoint/music and /mntpoint/video respectively.  Like perhaps some other people here, I assumed you had separate partitions for /music and /video on the NAS.

---

### Post by nafihsus on 2010-11-14
Can someone help me forcing a rw mounting of the drive. The command  
```
sudo mount -n -o remount,rw /dev/sda1 /mnt/point
```
is accepted by the system but still doesn't allow me to write resp. change file attributes in the directory.

Here is the content of my fstab which worked fine until recently:
```
$ cat /etc/fstab
eldenas:/music  /mnt/nas-music  nfs
eldenas:/video  /mnt/nas-video  nfs
eldenas:/pictures  /mnt/nas-pictures nfs
UUID=5e1448d5-05dc-47cc-8be6-bfd05e5d3c2c /home ext3 defaults 0 2
UUID=21fbc0e2-a502-4079-b00e-6b1920fde765 swap swap sw 0 0
UUID=b1885928-69af-44d5-a161-53f8b23be031 / ext3 defaults 0 1
```

I can write to the directory from Win 7!

---

### Post by SeijiSensei on 2010-11-14
> **nafihsus said:**
> Here is the content of my fstab which worked fine until recently:

Which one of those is /dev/sda1?

> I can write to the directory from Win 7!

Unless you installed the ext2/ext3 driver in Windows, it's highly unlikely that directory is part of an ext3 filesystem.  It's probably a Windows partition using NTFS.

---

### Post by nafihsus on 2010-11-16
/dev/sda1 and /dev/sda2 are the windows partitions (ntfs).
The QNAP NAS does not appear in gparted.

---

