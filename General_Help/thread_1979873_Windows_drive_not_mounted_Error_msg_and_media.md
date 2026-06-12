---
title: "Windows drive not mounted? Error msg and media"
date: 2012-05-14
forum: General Help
---

### Post by bradlees on 2012-05-14
I have a laptop that dual boots windows 7 and ubuntu 11.10. Recently, ubunut will not mount the windows partitions. I get some drive error message. I used to share files by dragging them between the os'es. Is there any way to fix this?
 
Furthermore, what is the best way to store media files that you want to share between os'es? Create some type of partition for these?

---

### Post by coffeecat on 2012-05-14
> **bradlees said:**
> Recently, ubunut will not mount the windows partitions. I get some drive error message.

Please post the exact error message. This will help to see what may be going on. Are you able to boot into Windows? You mention Windows partitions in the plural; is that a typo or do you have more than one?

> **bradlees said:**
>  I used to share files by dragging them between the os'es. Is there any way to fix this?

It's not a good idea to write to your Windows C: partition routinely, so...
 
> **bradlees said:**
> Furthermore, what is the best way to store media files that you want to share between os'es? Create some type of partition for these?

It's better to have a separate partition formatted NTFS for sharing files between Windows and Ubuntu in a dual-boot. Post the output of these terminal commands and we can see what your setup is like:

```
sudo fdisk -lu
sudo blkid
mount
```

Highlight the output with the mouse and then right-click for copying the output for pasting into your post.

---

### Post by Mark Phelps on 2012-05-14
Unfortunately, updating files/folders inside Win7 OS partition from outside (i.e., using Ubuntu) CAN result in filesystem corruption.  Which is likely what happened to you.

The simple fix is to boot into Windows and run CHKDSK, but if you can't boot, this becomes a serious problem.

If you have access to a Windows PC, you can download the free version of Partition Wizard boot CD, burn that to CD, boot your PC from it, and use IT to run a CHECK on the3 Win7 OS partition.

Hopefully, that will fix the filesystem.

And in future, if you want to share files between OSs, a much better solution is to have a separate NTFS data partition.  That way, you don't risk getting boot problems in Windows.

---

### Post by bradlees on 2012-05-15
> **coffeecat said:**
> Please post the exact error message. This will help to see what may be going on. Are you able to boot into Windows? You mention Windows partitions in the plural; is that a typo or do you have more than one?



It's not a good idea to write to your Windows C: partition routinely, so...
 


It's better to have a separate partition formatted NTFS for sharing files between Windows and Ubuntu in a dual-boot. Post the output of these terminal commands and we can see what your setup is like:

```
sudo fdisk -lu
sudo blkid
mount
```Highlight the output with the mouse and then right-click for copying the output for pasting into your post.

I get a long error message about sda2 that I don't know how to copy that says a lot about record has wrong sequence, inode corrupt: input/output error, then cluster accounting failed.  

as for the other command:

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2a6dc38b

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      616447      307200    7  HPFS/NTFS/exFAT
/dev/sda2          616448   335061728   167222640+   7  HPFS/NTFS/exFAT
/dev/sda3       589498368   620955647    15728640    7  HPFS/NTFS/exFAT
/dev/sda4       335063038   589498367   127217665    5  Extended
/dev/sda5       335063040   585846783   125391872   83  Linux
/dev/sda6       585848832   589498367     1824768   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 3965 MB, 3965190144 bytes
49 heads, 48 sectors/track, 3292 cylinders, total 7744512 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            8192     7744511     3868160    b  W95 FAT32

and:

/dev/sda1: LABEL="SYSTEM" UUID="B0E89518E894DE42" TYPE="ntfs" 
/dev/sda2: UUID="00AC6E8AAC6E7A54" TYPE="ntfs" 
/dev/sda3: LABEL="HP_RECOVERY" UUID="00FEA72DFEA71A44" TYPE="ntfs" 
/dev/sda5: UUID="d6f8412b-3eb4-4bad-b742-84938e6060d0" TYPE="ext4" 
/dev/sda6: UUID="065e00f4-3841-4019-9032-c970954c9e23" TYPE="swap" 
/dev/sdb1: UUID="3561-6361" TYPE="vfat"

and:

/dev/sda5 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ben/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ben)
/dev/sdb1 on /media/3561-6361 type vfat (rw,nosuid,nodev,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush,uhelper=udisks)

Thanks for looking

---

### Post by bradlees on 2012-05-15
I don't have a problem booting either os. I just used to drag and drop between the two. As I now know to avoid this, I will create a new partition for the media. I can use gparted?

---

### Post by coffeecat on 2012-05-15
> **bradlees said:**
> I get a long error message about sda2 that I don't know how to copy that says a lot about record has wrong sequence, inode corrupt: input/output error, then cluster accounting failed.  


Even though you say you can boot into Windows, I suggest you do a chkdsk on your C: partition as Mark Phelps suggests.

Yes, you can create a partition with Gparted, but you have a problem. Your partition layout at the moment is:

sda1 - Windows 7 system/boot partition. About 300MB
sda2 - (probably) Windows C: partition - about 167GB
sda3 - HP Recovery partition - about 16GB
sda4 - Extended partition - about 127GB 
sda5 - Ubuntu root partition (logical) - about 125GB
sda6 - Ubuntu swap partition (logical) - about 2GB

The sda3 recovery partition comes physically after the extended sda4, and at the moment you have no space to create another partition. More trickily all your quota of four primary partitions has been used up - your extended sda4 partition is simply a special type of primary whose sole purpose is to act as a container for the logicals. 

If you do want to create a NTFS partition, the only immediately practical way is to shrink your Ubuntu root partition (which at 125 GB is somewhat large) and then create a NTFS partition in the freed space. But you would have to do this from the live CD. If you need help with this, post back.

Whatever you do, don't be tempted to allow Windows Disk Management to create dynamic partitions. This is a proprietary "solution" to the 4-primary partition limitation and Linux cannot work with Windows' dynamic partitions. You will dig a hole for yourself if you do this.

---

### Post by bradlees on 2012-05-15
> **coffeecat said:**
> Even though you say you can boot into Windows, I suggest you do a chkdsk on your C: partition as Mark Phelps suggests.

Yes, you can create a partition with Gparted, but you have a problem. Your partition layout at the moment is:

sda1 - Windows 7 system/boot partition. About 300MB
sda2 - (probably) Windows C: partition - about 167GB
sda3 - HP Recovery partition - about 16GB
sda4 - Extended partition - about 127GB 
sda5 - Ubuntu root partition (logical) - about 125GB
sda6 - Ubuntu swap partition (logical) - about 2GB

The sda3 recovery partition comes physically after the extended sda4, and at the moment you have no space to create another partition. More trickily all your quota of four primary partitions has been used up - your extended sda4 partition is simply a special type of primary whose sole purpose is to act as a container for the logicals. 

If you do want to create a NTFS partition, the only immediately practical way is to shrink your Ubuntu root partition (which at 125 GB is somewhat large) and then create a NTFS partition in the freed space. But you would have to do this from the live CD. If you need help with this, post back.

Whatever you do, don't be tempted to allow Windows Disk Management to create dynamic partitions. This is a proprietary "solution" to the 4-primary partition limitation and Linux cannot work with Windows' dynamic partitions. You will dig a hole for yourself if you do this.

I would not have a problem with reinstalling ubuntu with a new partition set up as that sounds like the best idea at this point. Any pointers on a better way to configure the dual boot set up would be appreciated.

Thanks

---

### Post by coffeecat on 2012-05-16
> **bradlees said:**
> I would not have a problem with reinstalling ubuntu with a new partition set up as that sounds like the best idea at this point. Any pointers on a better way to configure the dual boot set up would be appreciated.

Thanks

I don't see any need to re-install. Your partition manipulation would be the same whether you re-installed or not. Your partitions go in this order physically:

sda1
sda2
sda4 - containing:
 - sda5
 - sda6
sda3

The only ways to add another NTFS partition, which would have to be a logical one inside sda4, are to:

1 - shrink sda5 and use the freed space, or:

2 - shrink sda2 and then enlarge sda4 into the freed space, after which you could create a logical NTFS partition at the beginning of the extended partition, or:

3 - a combination of the two, shrinking both sda2 and sda5 to give space to make a really big new data partition.

Caveats:

[list][*]If you choose to shrink sda2, use the Windows 7 Disk Management utility for this and run the chkdsk utility on your C: partition 3 times before you do so to make sure there is no filesystem corruption. Despite being able to boot into Windows, the errors you saw on trying to mount sda2 are worrying.
[*]In order to enlarge sda4, or shrink sda5 and also to create the new partition, use Gparted from the live Ubuntu CD/USB. You cannot do this from a running Ubuntu in sda5. Also, when you first open Gparted in the live CD, right-click on sda6 and choose "swapoff" otherwise you'll find that sda4/5/6 are locked.
[*]Shrinking partitions can take a long time, particularly if you resize from the front end.
[*]Backup and backup again. You are manipulating partitions with data on them. There is a risk of something going wrong. I suggest also that you do an image of your Windows system with something like Acronis or Macrium Reflect (free). It sounds as though your Ubuntu system is disposable if you don't mind re-installing, but if Your Windows needs to be re-installed from the recovery partition, you will lose all your applications and settings.
[/list]

---

### Post by bradlees on 2012-05-25
This may be a dumb question, and possibly one that is answered somewhere else, but I have created a new ntsf partition around 80gb. I would like to use this for media (pics, videos, and music) shared between os's. Mainly, I want to sync my music library between the two systems. What is the best way to do this?

---

### Post by oldfred on 2012-05-25
I use a shared NTFS with my XP and have Firefox, Thunderbird profiles and photos & data in that partition. I still use that shared even though I do not use XP hardly at all anymore.

You can mount it several ways.  I like to hide the mount in /mnt/shared, but many like it in /media/shared. The main difference is in /media it shows in left panel of Nautilus and in /mnt it does not. But with folders all linked the Nautilus enty is superfluous. 

Use template and copy entry into fstab:
[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)

New versions of NTFS-3g
[http://b.andre.pagesperso-orange.fr/permissions.html](http://b.andre.pagesperso-orange.fr/permissions.html)
Older systems with older version of NTFS-3g: Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)
HOWTO: Mount NTFS partitions with specific ownership/permissions - WorMzy
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)

Then you can create links to folders in you mount into /home.

Shared /data (NTFS)-see post #3 oldfred
[http://ubuntuforums.org/showthread.php?t=1772620](http://ubuntuforums.org/showthread.php?t=1772620)
Mount, hide & link windows partition
[http://ubuntuforums.org/showthread.php?t=1397508](http://ubuntuforums.org/showthread.php?t=1397508)

---

### Post by Morbius1 on 2012-05-25
> **oldfred said:**
> New versions of NTFS-3g
[http://b.andre.pagesperso-orange.fr/permissions.html](http://b.andre.pagesperso-orange.fr/permissions.html)

I don't know if I can adequately express the caution one should use before implementing the use of the "permissions" option for ntfs. If you are dual booting you need to tread carefully with this:

** Adding "permissions" and then actually mounting the partition is the last step. A pre-step is missing and it has to do with creating a table that links a Linux user's name to a Windows' user's name. Without that crucial step something like this can happen:

[http://askubuntu.com/questions/92863/mount-ntfs-partition-at-startup-with-non-root-user-as-owner](http://askubuntu.com/questions/92863/mount-ntfs-partition-at-startup-with-non-root-user-as-owner)
> OK, I got everything working on the Ubuntu side, with the following options: nls=iso8859-1,permissions,users,auto,exec

However, when I try to access files on the partition from Windows, the security settings are all messed up. On all the files (of those few I've examined) a new account called Account Unknown(long GUID) has been added to the list of users, and has full rights. Rigths for most other users are decreased so that I don't have rights to do stuff I expect. Notably "Everyone" does no longer seem to have right to "Traverse folder / execute".** It also creates a tunnel of sorts into in inner workings of the ntfs filesystem ( which is what allows you to do a chown or chmod on ntfs ) that doesn't really happen in the normal more conventional way of mounting an ntfs partition which creates a "view" of that partition that makes it appear to have Linux permissions when in fact it does not.

It's just too risky to attempt and has to be maintained if new users are added or something like Samba is introduced into the mix. I would urge you not to recommend this method.

---

### Post by coffeecat on 2012-05-25
> **bradlees said:**
> This may be a dumb question, and possibly one that is answered somewhere else, but I have created a new ntsf partition around 80gb. I would like to use this for media (pics, videos, and music) shared between os's. Mainly, I want to sync my music library between the two systems. What is the best way to do this?

Two issues that I can see here. First, mounting the partition from both OSs. Second - syncing your music libraries.

**Mounting the partition**.

In Windows, it's easy. It will be picked up as D: or E: or whatever the next "drive" letter is, or you can change the drive designation, except I've forgotten how to do this.

In Ubuntu, you can either mount the partition on an as-needed basis from a Nautilus file browser window, or add an entry in /etc/fstab to have it mounted automatically on bootup. Oldfred has given you some good links, but if you need help with fstab, post the output of these three commands (we need fdisk and blkid again because you have added a partition):

```
sudo fdisk -lu
sudo blkid
cat /etc/fstab
```

With that output, either oldfred or Morbius1 or I can help you with a suitable edit to /etc/fstab. Once you have the partition visible in both OSs, you can create your folder layout in either and all saved files will be visible in both, with a couple of caveats:

[list][*]Don't save files from Ubuntu to your NTFS partition while Windows is hibernated. As soon as Windows is reawoken it will restore the filesystem to the state it was in before hibernation and you will not be able to access them (at least from Windows).
[*]Use the "windows_names" mount option in /etc/fstab (I know Morbius1 agrees about this) otherwise Ubuntu will happily save files with forbidden characters. Ubuntu will equally happily display them for you but Windows will not be at all happy.[/list]

**Syncing your music libraries**

It really depends on what music software you are using and as I have limited experience of some, I can only voice some general concerns. If you are using Banshee in Ubuntu, then you can simply add your music files to its playlists by pointing it at the folders where the music files are. I believe that's true of Rhythmbox - which is the default music player in 12.04 - but I'm one of those strange people who actually prefer Banshee, so I'm not 100% sure. We all have our faults, but there you go! :wink:

If you are using iTunes in Windows, there may be a complicating factor. My brief experience of iTunes in MacOS (enough to convince me that I do not like it) revealed that it copies all your music files in a sort-of hyperactive Mary Poppins fashion into folders hidden deep somewhere in your home folder. Spit, spot! I think it does the same in Windows. So - if you are using iTunes in Windows and Banshee/Rhythmbox in Ubuntu, you need to take that into consideration. And if you are also wanting to sync with an iPod or other MP3 player - there's another complication.

Or have I misunderstood you?

---

