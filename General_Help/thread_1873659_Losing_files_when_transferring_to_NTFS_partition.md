---
title: "Losing files when transferring to NTFS partition"
date: 2011-11-01
forum: General Help
---

### Post by banosd on 2011-11-01
I have had a dual boot set up with Ubuntu and Windows 7 for over one year and after upgrading to Oneiric, I am noticing that I am immediately losing files transferring from Ubuntu to folders on my Windows 7 partition.  I have shortcuts set up that reside in my Nautilus folders.  Could this be the problem?  I don't know what is happening to these files, they completely disappear.

---

### Post by dcstar on 2011-11-02
> **banosd said:**
> I have had a dual boot set up with Ubuntu and Windows 7 for over one year and after upgrading to Oneiric, I am noticing that I am immediately losing files transferring from Ubuntu to folders on my Windows 7 partition.  I have shortcuts set up that reside in my Nautilus folders.  Could this be the problem?  I don't know what is happening to these files, they completely disappear.

You cannot "transfer" Linux specific things to non-Linux filesystems. Be more specific about what you are "losing".

---

### Post by Rubi1200 on 2011-11-02
It could be a permissions issue, but as dcstar rightly pointed out, we need to know exactly what files you are losing.

Thanks.

---

### Post by mastablasta on 2011-11-02
> **dcstar said:**
> You cannot "transfer" Linux specific things to non-Linux filesystems. Be more specific about what you are "losing".
 
that doens't really make sense at all. files are files are 1 and 0's. if you can transfer them to DVD filestem or FAT32 key you could just as well transfer them to NTFS or whatever other file syste you are using as long as propper tools are used to do this.
 
another thing of course is if one would try to transfer any system files. that would not be alowed.
 
more info required.

---

### Post by Morbius1 on 2011-11-02
> **banosd said:**
> I have had a dual boot set up with Ubuntu and Windows 7 for over one year and after upgrading to Oneiric, I am noticing that I am immediately losing files transferring from Ubuntu to folders on my Windows 7 partition.  I have shortcuts set up that reside in my Nautilus folders.  Could this be the problem?  I don't know what is happening to these files, they completely disappear.

Are these files disappearing while you are still running Linux?

I suppose this could be a permissions issue but I would think you would get an error message telling you that if this was the case.

Or are these files disappearing when you log back into Windows?

That's a completely different problem and one that has a solution if it has to do with "special characters" in the file name. You would have to specifically enter an entry in fstab to auto mount this partition and add an option called "windows_names" that prevents you in Linux from saving a file with a name that Windows cannot interpret.

---

### Post by Mark Phelps on 2011-11-02
Are you hibernating or sleeping your Windows setup? If so, STOP transferring files that, as that will NOT work.

---

### Post by banosd on 2011-11-03
Here are the files:

Documents and media that I have downloaded in Linux.

A movie I downloaded with Transmission.  I copied it over to my shortcut to my Windows Videos folder.  Disappeared completely!

Even updating a document in Libre Office, I saved it to my Windows Documents folder...now its gone

THis has been going on for a week now, everything I am copying over just disappears.

Maybe it is a problem with permissions of the shortcuts.  If so, how do I eliminate them?  This was not an issue with Karmic.

Thanks for the answers so far, gentlemen

FYI, I examined the permissions of my shortcuts, they say root.  Is it something that needs to be changed in fstab?  I had ntfsconfig configure the drive for me, I never edited it directly

---

### Post by Morbius1 on 2011-11-03
Why not post the output of each of the following commands so we can all see if this is a mounting, permissions, or something else problem:
```
sudo blkid -c /dev/null
cat /etc/fstab
mount
```

---

### Post by banosd on 2011-11-04
banosd@UL50AT:~$ sudo blkid -c /dev/null
[sudo] password for banosd: 
/dev/sda1: LABEL="400GB" UUID="AAD05528D054FBCF" TYPE="ntfs" 
/dev/sda5: UUID="5a42d132-bb8f-46af-a14b-eb3dd192761e" TYPE="swap" 
/dev/sda6: UUID="0fd2d981-c326-47da-8174-669162a0f742" TYPE="ext4" 
/dev/sda7: UUID="b47638ef-4d1d-4680-91fd-1c9c89073a3e" TYPE="swap" 
/dev/sdb1: LABEL="16GB" UUID="0A862DB2862D9EE7" TYPE="ntfs" 
/dev/sdd1: LABEL="System Reserved" UUID="48D6BAA2D6BA9024" TYPE="ntfs" 
/dev/sdd2: LABEL="750GB" UUID="48D0BE81D0BE74B2" TYPE="ntfs" 
banosd@UL50AT:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
/dev/sda6	/	ext4	errors=remount-ro	0	1
/dev/sda1	/media/400GB	ntfs-3g	defaults,locale=en_US.UTF-8	0	0
/dev/sda7	none	swap	sw	0	0


banosd@UL50AT:~$ mount
/dev/sda6 on / type ext4 (rw,errors=remount-ro,commit=0)
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
/dev/sda1 on /media/400GB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/banosd/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=banosd)
/dev/sdb1 on /media/16GB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd1 on /media/System Reserved type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sdd2 on /media/750GB type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)

Come to think of it, I do remember seeing some fuseblk error once but don't remember what it said

---

### Post by Synoc on 2011-11-04
this MAY be an issue, I have heard of this before. NTFS doesn't get along with Linux, on occasion. you CAN write to it and you can pull from it. but it may not journal the new files, so if you boot  to Windows and Windows checks the journaling, an update could misplace your files. they may still be there but not accessible. my recomendation is to, if you don't need security between the two systems, is set up a FAT32 partition and use that for your share.  but this is just a thought.

---

### Post by Morbius1 on 2011-11-05
>  /dev/sda1    /media/400GB    ntfs-3g    defaults,locale=en_US.UTF-8    0    0There's actually nothing wrong with that line in fstab. It will mount that partition to /media/400GB with owner = root and permissions of 777 which will allow anyone to read, write, and execute anything on that partition.

[COLOR=Blue]**Note1**[/COLOR]: I sincerely hope that this is not the partition that holds your Windows OS. I'm kind of old school when it comes to allowing write access to the Windows system partition but that choice is up to you. Mark Phelps above will no doubt also post about the dangers of doing so.

**[COLOR=Blue]Note2[/COLOR]**: Speaking of Mark Phelps you never answered his question:
> Are you hibernating or sleeping your Windows setup? If so, STOP transferring files that, as that will NOT work.[COLOR=Blue]**Note3**[/COLOR]: Come to think of it you never answered my question either:
> Are these files disappearing while you are still running Linux? ... Or are these files disappearing when you log back into Windows?If they are disappearing when you reboot to Windows and they contain special characters then modify that line in fstab to this:
```
 /dev/sda1    /media/400GB    ntfs-3g    defaults,windows_names,locale=en_US.UTF-8    0    0
```Then unmount the partition:
```
sudo umount /media/400GB
```And remount it with the new fstab line:
```
sudo mount -a
```

---

### Post by banosd on 2011-11-06
I am hibernating in Win7 because its a laptop.

I don't think its a special character issue as I try to avoid that because I know I will be sharing most files between Ubuntu/Win 7

---

### Post by Morbius1 on 2011-11-06
Then as per Mark Phelps you have your answer.

Just did a quick search of the forum and found this a plausable explanation: [http://ubuntuforums.org/showthread.php?p=9291772#post9291772](http://ubuntuforums.org/showthread.php?p=9291772#post9291772)

> The reason this happens is that when you hibernate Windows, it writes  the system state to a file stored on disk, so that when you bring the  system back up, instead of having to go through a complete boot process,  the contents of the saved system state are loaded from the file - so  it's quicker.

If you boot Ubuntu after having put windows into hibernation and change  or create files on the windows partition, the saved system state file  will be unaware of those changes so they won't show.
It's quite possible there is some ntfs-3g option that covers this but I have no experience in it as I've never attempted to do what you are trying.

---

### Post by Mark Phelps on 2011-11-06
Aws long as you continue to Hibernate Windows, you will CONTINUE to have this problem -- regardless of what drivers or apps you install in Linux.

Why? Because this is what is SUPPOSED to happen -- Windows will restore the exact state the PC was in when it was Hibernated -- including the drives.

So, as I said earlier, if you insist on making changes to partitions that you access while in Windows, you will have to STOP hibernating.

---

### Post by dcstar on 2011-11-07
> **Mark Phelps said:**
> Aws long as you continue to Hibernate Windows, you will CONTINUE to have this problem -- regardless of what drivers or apps you install in Linux.

Why? Because this is what is SUPPOSED to happen -- Windows will restore the exact state the PC was in when it was Hibernated -- including the drives.

So, as I said earlier, if you insist on making changes to partitions that you access while in Windows, you will have to STOP hibernating.

And if you let Linux overwrite data on the Windows partition, then Windows will not know that the file has changed and you could end up with a totally corrupted Windows system.

I wonder if the "fuseblk error" the OP can't remember was something like "Do not use Hibernated NTFS partitions" etc.?

---

