---
title: "Losing data when writing to NTFS partition."
date: 2012-03-13
forum: General Help
---

### Post by ToshibaLaptoplinux on 2012-03-13
So there is one HUGE problem I have encountered which resulted in my losing some pretty critical data.

I have set up my laptop so that it is dual boot, Windows 7 and Ubuntu 11.10 64bit. They are sharing a 50 GiB ntfs partition that is mounted as D: in Windows and /Windows_D in Ubuntu.

1) I can see the partition from both OS's
2) Data that I write to that directory from Windows can be seen and edited in Ubuntu.
3) If I write data to the ntfs partition from Ubuntu, it seems to move or copy successfully and I can work with the data, however...

If I reboot, either into Windows or Ubuntu, the data disappears!!! Poof! Up in smoke! Gone. Not happy.

I noticed it first with some critical data I transferred which is now lost and I have run multiple tests creating, copying, moving various kinds of documents to the partition and the behaviour is reproducible. Upon reboot into either OS the data is GONE.

I am baffled as I have run this setup successfuly on multiple iiterations of Ubuntu. The only thing I can think of that is different with my 11.10 install vs the previous ones is that it is 64bit and my home is encrypted.

As I said the behaviour is consistent and reproducible. It also occurs if using Midnight Commander to move data which leads me to believe that it isn't just a Nautilus issue.

What is going on and how do I troubleshoot this?

Is there any possibility of recovering data that went into that blackhole?

What information do I need to provide in submitting a bug report? It is pretty clear to me that it is a bug on the Ubuntu side but I don't know how to isolate the package to use apport. I guess it would be whatever Ubuntu uses to talk to NTFS volumes?

---

### Post by Mark Phelps on 2012-03-13
When you boot into Ubuntu, have you put Win7 to SLEEP or HIBERNATE it? IF so, do NOT make changes to the shared data drive with Win7 in that state.  Win7 stores away the directory catalog of the shared drive such that, when it is reawakened, it rewrites it -- effectively returning the filesystem to its old state.

If you want to share data, then you will have to Shut Down Win7 before you boot into Ubuntu.

Sorry, but that's necessary with dual-boot systems and shared filesystems.

---

### Post by ToshibaLaptoplinux on 2012-03-16
> **Mark Phelps said:**
> When you boot into Ubuntu, have you put Win7 to SLEEP or HIBERNATE it? IF so, do NOT make changes to the shared data drive with Win7 in that state.  Win7 stores away the directory catalog of the shared drive such that, when it is reawakened, it rewrites it -- effectively returning the filesystem to its old state.

If you want to share data, then you will have to Shut Down Win7 before you boot into Ubuntu.

Sorry, but that's necessary with dual-boot systems and shared filesystems.

Thanks for the information. That is good to know as I was unaware of that.

However, That is **not** the case in my sitaution. Windows is fully shutdown when I am working in Ubuntu.

Any other ideas? Clearly this problem totally defeats the purpose of having a shared partition in a dual boot box.

---

### Post by dcstar on 2012-03-16
> **ToshibaLaptoplinux said:**
> Thanks for the information. That is good to know as I was unaware of that.

However, That is **not** the case in my sitaution. Windows is fully shutdown when I am working in Ubuntu.

Any other ideas? Clearly this problem totally defeats the purpose of having a shared partition in a dual boot box.

If the Windows partition is a Dynamic partition then all bets are off. It has to be a Basic partition.

---

### Post by sudodus on 2012-03-16
This is a new problem for me. I am reading and learning from the experienced guys ...

---

### Post by dragonfly41 on 2012-03-16
> If the Windows partition is a Dynamic partition then all bets are off. It has to be a Basic partition.Does this mean that shared NTFS partition (shared between Win and Ubuntu) must not be in a logical partition as distinct from a primary partition?   Why is this?   I've got that configuration (NTFS format of extended logical partition) and I may have to change based on above advice.

---

### Post by Mark Phelps on 2012-03-16
> **ToshibaLaptoplinux said:**
> ... Clearly this problem totally defeats the purpose of having a shared partition in a dual boot box.

You're certainly right about that!

I used shared NTFS partitions all the time, so it's not a basic problem with the approach.

Only suggestion I have is to run CHKDSK on the shared partition next time you are in Win7.  That's all I can think of at this point.

---

### Post by oldfred on 2012-03-16
+1 on running chkdsk.

Ubuntu runs fsck every 40 or 60 reboots. I do not think Windows runs chkdsk unless you run it manually which you should.

The NTFS-3G driver is not Ubuntu per se but a separate development. I would think any bug would have to be filed against it unless it is somehow related to how Ubuntu is using it. I have used NTFS shared data partition with XP for years without issue. My Firefox & Thunderbird profiles are in the NTFS partition so it gets lots of use.

You can try to recover data, but it can be a long process, I think Mark also has suggestions on Windows recovery tools. I have used photorec and it found every file & some files that were saved many times found all the old versions. Only recovers file extension, so a lot of work to figure out what is really worth saving.

gddrescue, Scalpel, magic rescue, photorec, foremost, sleuthkit & others
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
[http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/)

Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Use scripts to help sort files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by dandnsmith on 2012-03-16
> **dcstar said:**
> If the Windows partition is a Dynamic partition then all bets are off. It has to be a Basic partition.

Just in passing, a dynamic partition isn't the same as a logical partition.

---

### Post by dragonfly41 on 2012-03-16
So I now understand ..

[https://bto.bluecoat.com/packetguide/8.4/nav/tasks/partition/create-partition-dynamic.htm](https://bto.bluecoat.com/packetguide/8.4/nav/tasks/partition/create-partition-dynamic.htm)

---

### Post by dave2001 on 2012-03-16
See my posts in your OTHER thread.. don't feel like writing it again.

---

### Post by Rebelli0us on 2012-03-16
Your setup should work fine. You must have done something, perhaps encrypted or dynamic partition?

---

### Post by ToshibaLaptoplinux on 2012-03-23
> **Rebelli0us said:**
> Your setup should work fine. You must have done something, perhaps encrypted or dynamic partition?



The NTFS partition is not encrypted however my Ubuntu HOME partition is encrypted.

I don't believe that the NTFS partition is dynamic. I set up all partitions in Win7 before installing Ubuntu upon recommendation of the Ubuntu How-To.

How would one verify that a partition is, or is not, a dynamic partition?

---

### Post by dcstar on 2012-03-23
> **ToshibaLaptoplinux said:**
> 
..........
How would one verify that a partition is, or is not, a dynamic partition?

By using the Windows Disk Manager.

---

### Post by Morbius1 on 2012-03-23
Would it be possible to provide some basic data on how you are set up in Linux by posting the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```

---

### Post by ToshibaLaptoplinux on 2012-04-26
> **Morbius1 said:**
> Would it be possible to provide some basic data on how you are set up in Linux by posting the output of the following commands:
```
sudo blkid -c /dev/null
``````
cat /etc/fstab
``````
mount
```

> sudo blkid -c /dev/null
/dev/sda1: LABEL="SYSTEM" UUID="4C34D0CD34D0BB62" TYPE="ntfs" 
/dev/sda2: UUID="8E2029AB20299B6B" TYPE="ntfs" 
/dev/sda4: LABEL="SAMSUNG_REC" UUID="AA64B59864B56829" TYPE="ntfs" 
/dev/sda5: UUID="E01699A316997B6C" TYPE="ntfs" 
/dev/sda6: UUID="03161f5b-215f-4414-9cf1-46ca1454dc47" TYPE="ext4" 
/dev/sda7: UUID="7fee7c6c-648e-4ad8-b997-74259394a250" TYPE="ext4" 
/dev/sda8: UUID="4482fb9d-9450-4394-b3d2-73a04d6ee937" TYPE="ext4" 
/dev/mapper/cryptswap1: UUID="1bb34ec9-9bf5-43c4-a482-f56b1c308fb3" TYPE="swap"


> cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda8 during installation
UUID=4482fb9d-9450-4394-b3d2-73a04d6ee937 /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda7 during installation
UUID=7fee7c6c-648e-4ad8-b997-74259394a250 /boot           ext4    defaults        0       2
# /home was on /dev/sda6 during installation
UUID=03161f5b-215f-4414-9cf1-46ca1454dc47 /home           ext4    defaults        0       2
# /windows_D was on /dev/sda5 during installation
UUID=E01699A316997B6C /windows_D      ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda9 during installation
#UUID=c1cb43e9-fa11-4fd7-aaf6-4da8c41ff613 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0


> mount
/dev/sda8 on / type ext4 (rw,errors=remount-ro,commit=0)
proc on /proc type proc (rw,noexec,nosuid,nodev)
sysfs on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type devtmpfs (rw,mode=0755)
devpts on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
tmpfs on /run type tmpfs (rw,noexec,nosuid,size=10%,mode=0755)
none on /run/lock type tmpfs (rw,noexec,nosuid,nodev,size=5242880)
none on /run/shm type tmpfs (rw,nosuid,nodev)
/dev/sda7 on /boot type ext4 (rw,commit=0)
/dev/sda5 on /windows_D type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sda6 on /home type ext4 (rw,commit=0)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
/home/***/.Private on /home/*** type ecryptfs (ecryptfs_check_dev_ruid,ecryptfs_cipher=aes,ecryptfs_key_bytes=16,ecryptfs_unlink_sigs,ecryptfs_sig=b1d5d61746777de9,ecryptfs_fnek_sig=548c1cbb444dfcc9)
gvfs-fuse-daemon on /home/***/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=***)


I am stumped. I did a clean install and the behaviour is exactly the same.

I checked in the Windows 7 Disk Management Tool and as best I can tell it is not a Dynamic Partition.

The good news is that the Windows chkdsk utility recovered all of the "missing" files. However, it is worth noting that I first attempted recovery with the linux tools suggested in the thread and none of them found the files.

Any suggestions in terms of next steps?

---

### Post by Morbius1 on 2012-04-26
I personally have never experienced this problem per se. But as described by Mark Phelps above:
> When you boot into Ubuntu, have you put Win7 to SLEEP or HIBERNATE it? IF so, do NOT make changes to the shared data drive with Win7 in that state. Win7 stores away the directory catalog of the shared drive such that, when it is reawakened, it rewrites it -- effectively returning the filesystem to its old state.
Another phenomenon is invalid characters in the file name that Linux can write to an ntfs partition that is totally fine with Linux but ones that a WindowsOS cannot read. You can prevent Linux from naming these files with invalid characters by changing your fstab entry to this:
> UUID=E01699A316997B6C /windows_D      ntfs    defaults,umask=007,gid=46[COLOR=Blue]**,windows_names**[/COLOR] 0       0

---

### Post by ToshibaLaptoplinux on 2012-04-27
> **Morbius1 said:**
> I personally have never experienced this problem per se. But as described by Mark Phelps above:
Another phenomenon is invalid characters in the file name that Linux can write to an ntfs partition that is totally fine with Linux but ones that a WindowsOS cannot read. You can prevent Linux from naming these files with invalid characters by changing your fstab entry to this:

Thanks Morbius. The fstab tip is a good one. However I would note that neither OS is in a sleep or hibernate state. I am doing full reboots.

The only thing that I can think of is that my home is encrypted. But the behaviour is still the same even if I create documents and directories working directly in the NTFS partition.

---

### Post by Rebelli0us on 2012-04-27
> **Morbius1 said:**
> I personally have never experienced this problem per se. But as described by Mark Phelps above:
Another phenomenon is invalid characters in the file name that Linux can write to an ntfs partition that is totally fine with Linux but ones that a WindowsOS cannot read. You can prevent Linux from naming these files with invalid characters by changing your fstab entry to this:

UUID=E01699A316997B6C /windows_D ntfs defaults,umask=007,gid=46,**windows_name**s 0 0 


Linux creates illegal filenames on NTFS partitions, will the "**windows_name**" option prevent that?

I have hundreds of these, from browser bookmarks, saved Youtube European movies with non-western(?) characters. You can open Nautilus and create a new file named “\\new> file |” or 2 files named “FileName” and “filename”. Here's what they look like:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=216710&stc=1&d=1335548227[/IMG]

---

### Post by Morbius1 on 2012-04-27
That looks like a character encoding problem to me. THe "windows_names" option is pretty specific as to it's meaning:
> [B]windows_names
[/B]This option prevents files, directories and extended attributes to be created with a name not allowed by windows, either because it contains some not allowed character (which are the nine characters ” * / : < > ? \ | and those whose code is less than 0×20) or because the last character is a space or a dot. Existing such files can still be read (and renamed).

---

### Post by Rebelli0us on 2012-04-27
> **Morbius1 said:**
> That looks like a character encoding problem to me. THe "windows_names" option is pretty specific as to it's meaning:

True, some apps are not reading unicode filenames correctly. But if you work with German, Russian or Greek characters, Linux turns your NTFS partition into a garbage dump.

Here's a line from fstab, where does the option "**windows_names**" go? I never knew if these are comma-delimited arguments or what.

```
UUID=9C1C85111C64E88A     /media/U2_1  ntfs-3g  defaults,uid=1000,umask=077,locale=en_US.utf8  0  0  

```

---

### Post by Morbius1 on 2012-04-28
> I never knew if these are comma-delimited arguments or what.The are:
```
 UUID=9C1C85111C64E88A     /media/U2_1  ntfs-3g  defaults,uid=1000,umask=077,locale=en_US.utf8,windows_names  0  0
```

---

