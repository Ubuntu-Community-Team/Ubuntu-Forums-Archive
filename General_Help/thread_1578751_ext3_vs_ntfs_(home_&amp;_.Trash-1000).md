---
title: "ext3 vs ntfs (/home &amp; .Trash-1000)"
date: 2010-09-20
forum: General Help
---

### Post by UncleBoarder on 2010-09-20
I'm moving my /home directory to my second drive.  Should it be NTFS or EXT3?

NTFS - I've read this is a bad idea but I don't know why.  It appears to work

EXT3 - Can't mount with a userID therefore can't put files in trash, must delete immediately.

It seems NTFS is a better choice but I need input on why it would be bad to have my /home on NTFS?

Is it a multi user thing?  I'm the only user.

---

### Post by robsoles on 2010-09-21
I am pretty sure /home requires a file system with users and permissions. I don't think NTFS cuts the grade well enough. I've been wrong before, it's how I learn more.

I will be miserable later if I hear you tried mounting an NTFS partition as /home without making a complete backup of all the data from your /home directory that you want to keep. Proper backups go on alternative media (ie, other hard disk or DVD(s) or USB(s)). :)

I've found ext4 very operable, is there a reason you can't use ext4 there?

---

### Post by TNT1 on 2010-09-21
ext4 FTW.

---

### Post by davrosuk on 2010-09-21
I'd go with ext4. Don't get me wrong, NTFS is very good... on Windows. But I'd rather use an FS built for Linux when using Linux. And performance wise ext4 beats NTFS.

---

### Post by WorMzy on 2010-09-21
/home should be a linux filesystem, ext# is the most prevalent these days, but there's nothing stopping you using ReiserFS, XFS, or JFS.

---

### Post by coffeecat on 2010-09-21
> **UncleBoarder said:**
> NTFS - I've read this is a bad idea but I don't know why.  It appears to work

There are several reasons why people might say it's a bad idea.

You can't use NTFS for a /home partition. As others have said, NTFS doesn't support Linux/Unix permissions. It's not just a bad idea - it won't work.

It's also a bad idea if you use NTFS when you don't have Windows available to repair it if need be. The Linux NTFS tools are simply not up to repairing a corrupted filesystem. You need Windows' chkdsk for that.

And some people might say NTFS is a bad idea simply because they are prejudiced against Microsoft and all its products. You can spot these people: they often use silly terms to describe Microsoft such as 'm$' or 'micro$haft'.

NTFS is a perfectly valid choice if you use it on a separate data partition or on a USB drive -_ but so long as you have Windows available for repair._ I use NTFS in this way - have done for some years - because it is a convenient way to share files between Linux and Windows. And it's a superior filesystem to FAT16/32, which many of the MS-haters are using each time they take a digital photo.

---

### Post by UncleBoarder on 2010-09-21
My goal is to share data on this volume between Ubuntu and Windows.  Windows drivers for EXT3 are available but not EXT4.  So that is pushing me to NTFS.  I'll do a follow up post after the attempt.

---

### Post by coffeecat on 2010-09-21
> **UncleBoarder said:**
> My goal is to share data on this volume between Ubuntu and Windows.  Windows drivers for EXT3 are available but not EXT4.  So that is pushing me to NTFS.  I'll do a follow up post after the attempt.

Then go for NTFS. You have Windows available should the filesystem need repairing and Ubuntu support for NTFS is good.

---

### Post by WorMzy on 2010-09-21
You could do what I do, have a separate data partition which I use to store all my documents/downloads/pictures/etc, and just use fstab to automount the storage partition, and mount --bind the directories that store those things over the top of the respective home folders. (Alternatively, you could use symlinks instead of mount --bind.)

So my ~/Downloads is actually /media/Terastore/Downloads, and ~/Videos is /media/Terastore/Videos, etc. The storage partition is NTFS, but my actual /home folder is EXT4, neatly avoiding the complications with file permissions.

This works fine on any Linux distribution, and the files are accessible from Windows too, so you can have several different OS' on the same PC, and still have your personal files waiting for you regardless of which one you boot into.

---

### Post by UncleBoarder on 2010-09-24
I couldn't get NTFS to work.  It booted and mounted with my home directory on the NTFS volume... but when I tried to launch firefox it gave me an error relating to permissions.  Sorry I lost the screen shot when I returned to ext3.  I couldn't get it to work.

---

### Post by robsoles on 2010-09-24
NTFS won't work as a container [COLOR=Red]f[/COLOR]or /home but you can make an NTFS file-space and share it with as many operating systems as you like, it's just not as defended as a good 'nix file-system would be.

---

### Post by coffeecat on 2010-09-25
> **robsoles said:**
> I am pretty sure /home requires a file system with users and permissions.

> **WorMzy said:**
> /home should be a linux filesystem

> **coffeecat said:**
> You can't use NTFS for a /home partition. As others have said, NTFS doesn't support Linux/Unix permissions. It's not just a bad idea - it won't work.

> **UncleBoarder said:**
> I couldn't get NTFS to work.  It booted and mounted with my home directory on the NTFS volume... but when I tried to launch firefox it gave me an error relating to permissions.

It sounds as though you mounted a NTFS filesystem as your /home. As you were told, this will not work. You can have your personal data on a separate NTFS partition - all your mp3s, videos, documents, and so on - but the /home directory must be on a Linux filesystem. When people mentioned NTFS for a separate data partition they meant a separate data partition, not a separate home partition. All the (hidden) configuration files, including the ones for Firefox, need a filesystem supporting Linux permissions.

**Edit:** just to clarify - if you have a separate data partition formatted NTFS, you still need your /home on your root partition. But you could set up symlinks in your /home linking to either the whole data partition or to individual folders in your data partition. These are analogous to Windows shortcuts. And you'd need to have the data partition mounted on bootup with a line in /etc/fstab if you create symlinks. Or you could not bother with symlinks and fstab and simply mount the partition from the Places menu as and when you needed it. With Windows seeing the partition as D: or E: or whatever, this is a convenient way to have personal files available to both OSs.

If you need help with fstab or creating the symlinks, do post back.

---

### Post by dcstar on 2010-09-25
> **coffeecat said:**
> 
.......
**Edit:** just to clarify - if you have a separate data partition formatted NTFS, you still need your /home on your root partition.
.......

No, "if you have a separate data partition formatted NTFS, you still need your /home on **a Linux** partition". There is no necessity for it to be in the "root" partition.

Linux does require full Linux filesystem support for /home and the first level of user folders below that, it may be possible to mount/symlink folders from the second level to NTFS but the results may be unpredictable.

---

### Post by coffeecat on 2010-09-25
> **dcstar said:**
> No, "if you have a separate data partition formatted NTFS, you still need your /home on **a Linux** partition". There is no necessity for it to be in the "root" partition.

Yes, I'm well aware of that. I was addressing the OP in the context of this particular thread, not experienced users. The OP is clearly unfamiliar with the gotchas that different filesystems and the Linux permissions system can trip the unwary with. To set up a separate /home partition and then symlink a separate NTFS partition to it would introduce a level of complexity that I'm sure the OP could do without.

As I was writing that edit, I realised that it was a simplification and wondered whether I should write "...you still need your /home on your root partition, or on a separate /home partition formatted with a Linux filesystem." But then I decided that would be over-pedantic in this particular situation. Even as I made my choice I had a sinking feeling that someone would pick me up on that. I should have listened to the sinking feeling. :rolleyes:

---

### Post by srs5694 on 2010-09-25
It's not clear how much data UncleBoarder wants or needs to share between Linux and Windows, vs. how much user data should be accessible to Linux alone. If there's to be a significant amount of Linux-only user data, then IMHO it makes sense to put /home on a separate partition (using a Linux filesystem, of course). This practice simplifies certain types of system upgrades and it simplifies certain types of backup operations.

If UncleBoarder wants *all* user data (aside from Linux program configuration files) to be accessible to both OSes, then there's relatively little benefit to splitting off /home. In that case, it makes sense to create an NTFS shared-data partition and mount it in /home/username/data (where "username" is the username on that system, assuming there's only one user) or some other location (which would be preferable if the system has multiple users). /home/username will then contain mostly just user-level program configuration files.

---

### Post by UncleBoarder on 2010-09-25
My goal was to put linux and windows data on an ext3 volume.  The reason I wanted home there as well was to conserve space on my root volume which is small.  And I figured both home and data could then grow as needed without having to predetermine the size of the home volume.

The reason for asking about NTFS is that for some reason when home is moved to the ext3 volume I can then no longer put things in the trash, they must be deleted immediately.  This is definately related to the home directory being place on the ext3 volume.  Prior to moving home, the Trash worked properly.

I have another thread listing that problem... no one has answered it.

[http://ubuntuforums.org/showthread.php?t=1580740](http://ubuntuforums.org/showthread.php?t=1580740)

---

