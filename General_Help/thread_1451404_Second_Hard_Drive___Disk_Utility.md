---
title: "Second Hard Drive /  Disk Utility"
date: 2010-04-10
forum: General Help
---

### Post by xtremedementor on 2010-04-10
Hi,

I have successfully installed 9.1 on my system which has 2 hard drives.

My question is how to format the second drive with disk utility?
Disk utility detects the drive no problem.
Also I would like the drive to mount at start up.

The options I have for formatting are:
FAT
Linux Ext2
Linux Ext3
Linux Ext4
Linux XFS
NTFS
Swap Space 
Empty

I also have the following options for the Partition Table:
Master Boot Record
GUID Partition Table
Don't Partition
Apple Partition Map

I just dont know what i should be selecting to add the second drive.

Also i am not particularly fussed about having a MS or Apple format as this is a Ubuntu Box.

Any help on this is greatly appreciated.

Thanks

---

### Post by srs5694 on 2010-04-10
> **xtremedementor said:**
> Hi,

I have successfully installed 9.1 on my system which has 2 hard drives.

My question is how to format the second drive with disk utility?
Disk utility detects the drive no problem.
Also I would like the drive to mount at start up.

First, please tell us how you intend to use the disk. Will you be storing a bazillion small files on it? (Word processing documents or MP3 files, say?) A smaller number of huge files? (Such as virtual machine disk images or AV recordings?) Will you be using it exclusively from Linux, or do you want to access it from another OS as well?

Generally speaking, ext2fs is useful only on small disks (under 1GB or so), since it lacks a journal; but this lack of a journal can be very important on such small disks, since the journal consumes disk space that might be better put to use storing files on small disks. Ext3fs and ReiserFS are both good choices for general-purpose Linux filesystems, with ReiserFS doing a better job on disks with large numbers of small files. JFS and XFS are well-regarded for big disks with large files. Ext4fs aims to be a good general-purpose filesystem (like ext3fs) but with improvements in handling large files (like JFS and XFS); however, it's still new and there are still occasional problem reports.

For mounting, that also depends on how you want to use the disk, and on how your current drive is configured. In many cases, it makes sense to mount a second disk as /home, but that's most easily handled at system installation time. I can't really offer better advice until I know more, such as your current partition layout (the output of "sudo fdisk -l" and "df -h" will be helpful) and what types of files you intend to store on the disk (user files, system files, a mail queue, DVR recordings, etc.).

> I also have the following options for the Partition Table:
Master Boot Record
GUID Partition Table
Don't Partition
Apple Partition Map

For a Linux-only system, I recommend the GUID Partition Table (GPT) format, since it's got some improvements over the older but more common Master Boot Record (MBR) format. Most importantly, GPT supports disks over 2TiB in size, whereas MBR maxes out at 2TiB (assuming the standard 512-byte sector size). This isn't an issue for most single disks, but it's critical for some RAID arrays. More minor, but more broadly useful, GPT improvements include partition names, backups of all important GPT data structures for improved reliability, checksum data to spot data corruption in partition definitions, and the elimination of the primary/extended/logical partition distinctions that causes so many problems with MBR. The main problem with GPT is that many older OSes don't support it, or provide only limited support. Windows Vista and 7 can both read and write GPT as data disks, but they can't boot from it on BIOS-based systems. Most versions of Windows XP and earlier can't handle GPT (although they can on some platforms; details are complex). Intel-based versions of Mac OS X use GPT by default.

That said, if you pick MBR, it's not the end of the world. MBR has been in use for years and does get the job done, at least on sub-2TiB disks. On such disks, GPT's improvements are fairly minor -- but worth taking advantage of, IMHO, if doing so is convenient.

---

### Post by xtremedementor on 2010-04-10
Hi,

Thanks for the response. I will be using the box as a basic file / media server.
Athe the moment it has 2 X 500GB drives. drive 1 is sharing the documents / music etc folders nicely on the network and i would like drive 2 to just be an extension to this.
This is being accessed by Xbox360, Win XP & Win 7, OSX (intel 10.5) and Linux (what can i say i like OS's)

The files will mainly be movies (2GB) Music and Photos (Film scans upto 250MB). The commonly used smaller files will be on drive 1 and the larger archive files will be on drive 2.


Remote access is also going to be implemented in the future.

Here are the outputs requested.

sudo fdisk -l

[I]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0060b82e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       60713   487677141   83  Linux
/dev/sda2           60714       60801      706860    5  Extended
/dev/sda5           60714       60801      706828+  82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000[/I]

I couldn't get an ouput from df-h.

Thanks again for any help.

---

### Post by srs5694 on 2010-04-10
It's "df -h", with a space between them; but that output is irrelevant, given the information you've already provided.

If I were designing a system from scratch to do what you describe, I'd use an entirely different partitioning system: I'd use a logical volume management (LVM) configuration, with a partition for /boot, LVM partitions on both disks, and various Linux partitions (root, /home, and possibly others) in the LVM spanning both disks. One important advantage of this configuration is that you can set aside one filesystem that's bigger than either of your disks to hold your data. It also gives you much greater flexibility to resize filesystems and add disk space in the future. Unfortunately, this type of configuration is tricky to set up with the standard Ubuntu desktop installer, since it doesn't support LVM, although some other Ubuntu variants do understand LVMs.

If you've done nothing more than set up Ubuntu already, you might consider re-installing using an LVM configuration. (Try Googling "Ubuntu LVM;" I found several guides that way, although I haven't studied them enough to recommend a specific one.) Alternatively, you could re-install with regular partitions, but create three on your first disk: One for the Ubuntu system files (root, or /; make it about 5-20GB, depending on how many packages you intend to install), one for your media files, and one for swap. You can then create one or more partitions on your second disk for additional media files. Keeping your media files in a separate partition from your OS installation gives you greater flexibility for handling upgrades in the future; you can install over your initial installation without damaging your media files.

Given the setup you've got now, or if you re-install using regular partitions, I'd say you should decide how you want to split up your data by directories. For instance, if you use /home/media for the files you share, you might have /home/media/movies, /home/media/music, and /home/media/photos. If you expect to devote as much space to movies as to music and photos, then you might mount the new drive at /home/media/movies, leaving the rest of /home/media on your existing root (/) filesystem. An appropriate /etc/fstab entry might look like this:

```

/dev/sdb1   /home/media/movies    xfs    defaults        0 2

```

This assumes you use XFS on the new partition; adjust it as necessary if you use something else.

---

### Post by xtremedementor on 2010-04-21
Hi again,

Sorry for not getting back sooner, been puting NBR on my netbook.

So far ubuntu is seeing the drive as an NTFS and i can manually mount it so for the moment that will do for me. Twonky and file shares are all working well with all devices.

I appreciate your help but it all seems a bit too much for a nOOb like me at the moment. I will revisit this when i have a little more experience with ubuntu.

For now i have enough to do to get pulseaudio playing nicely with skype and acidrip seeing my DVD as /dev/sr0 and not /dev/dvd/.

Thanks again for the great pointers. I will try them out on a fresh install after some more reading.

---

### Post by srs5694 on 2010-04-21
For a Linux-only system, I must *strongly* advise against using NTFS. If you have a power failure or system crash, your NTFS volume(s) will be inaccessible until they're checked with a Windows system and its CHKDSK utility. NTFS also lacks Unix-style permissions and ownership, which can be significant omissions on a Linux box, depending on how the disk is used. I don't have any benchmark data handy, but I expect that NTFS wouldn't perform as well as most Linux-native filesystems on a Linux box.

You can use the GUI GParted or the text-mode parted or mkfs to convert a partition from NTFS to use a Linux filesystem, such as ext3fs, ReiserFS, JFS, or XFS. This conversion will be destructive, though; the files on the converted partition will be lost.

---

### Post by xtremedementor on 2010-04-21
Thanks for the heads up on the NTFS.

At the moment the drive is empty as such so it would not be a big problem to change to a linux native partition.

I just feel i am not quite read for trying to set it as a mount point in home or re installing just yet.
For now i am just going to use it as a dump drive which will only be mounted for archiving. As i get more familiar with linux i will tackle this issue later. I think it would be wise to get a better understanding of the file systems and the workings of linux. I love the idea of linux and have tried a few times to change completely from win and osx but i think trying too much too soon has been my downfall in the past.

This time "softly softly catchy monkey" and i will be here to stay.

Thanks again for the quick responses and help. Its always appreciated.

---

