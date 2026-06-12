---
title: "ntfs drive seems to mount with different settings than found in fstab"
date: 2012-02-12
forum: General Help
---

### Post by moody_mark on 2012-02-12
Hi Folks,

I recently had a read of [this]("http://ubuntuforums.org/showthread.php?t=283131") thread and changed my fstab file to mount a ntfs drive but Im finding that it seems to be mounting with some other options all the time.

What im trying to achieve is this: I have several users on my machine, i wish to have the drive mounted as read write for some users but not for others, perhaps at a later date read only for some users.

Heres my fstab line the UUID is /dev/sdb1:

```
UUID=726716B4258E7766	/media/Data	ntfs-3g	rw,auto,uid=bob,gid=bob,fmask=0111,dmask=0000	0	0
```

However here's what mount is telling me

```
/dev/sdb1 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

Heres the UUIDs

```
sudo blkid
[sudo] password for bob: 
/dev/sda1: UUID="043C8AB63C8AA272" TYPE="ntfs" 
/dev/sdb1: LABEL="Data" UUID="726716B4258E7766" TYPE="ntfs" 
/dev/sdc1: UUID="2123fc36-25d4-4219-849f-1ada13a5dca8" TYPE="ext4" 
/dev/sdc5: UUID="6f01c26d-13ec-4d9c-9709-50686dd6ad34" TYPE="swap" 
/dev/sdd1: LABEL="FREECOM HDD" TYPE="vfat"
```

Im guessing im missing something obvious here?

---

### Post by Paddy Landau on 2012-02-13
Gosh, that thread is old.

**fmask** and **dmask** are for FAT, not for NTFS (see the *mount* manual). You can use **umask** instead.

**uid** and **gid** assign ownership of the mount, so assigning more than one person is not valid (in my tests, there is no error message, but the first one listed is used).

Thus, you can use only umask to achieve your effect of making the NTFS partition read-only.

Additionally, you explicitly said that you wanted it as rw (read-write) in your list of options. If you want it read-only, remove that item from the list of options.
```
UUID=726716B4258E7766  /media/Data  auto  defaults,ro,umask=0333  0  0
```Of course, that does not answer your question about how to make it read-only for some users and not for others.

Here is my suggestion, which works for me.

[LIST]
[*]Create a new group for the users who *are* allowed to write to the drive.
[*]Assign all the users who are allowed to write to the drive to that new group.
[*]Add gid to the list of options, using the new group, and umask=0002, as follows.```
UUID=726716B4258E7766  /media/Data  auto  defaults,gid=*yournewgroup*,umask=00002  0  0
```
[/LIST]
After rebooting, you should find that /media/Data is still owned by root but belongs to the new group.
```
[COLOR=Navy]ls -ld /media/Data[/COLOR]
drwxrwxr-x 1 root *yournewgroup* 4096 2012-02-13 13:36 /media/Data
```Then people in that group should be able to write to the device, whereas people not in the group should have read-only access.

Try it and let us know if it works.

---

### Post by moody_mark on 2012-02-14
> **Paddy Landau said:**
> 
[LIST]
[*]Create a new group for the users who *are* allowed to write to the drive.
[*]Assign all the users who are allowed to write to the drive to that new group.
[*]Add gid to the list of options, using the new group, and umask=0002, as follows.```
UUID=726716B4258E7766  /media/Data  auto  defaults,gid=*yournewgroup*,umask=00002  0  0
```
[/LIST]
After rebooting, you should find that /media/Data is still owned by root but belongs to the new group.
```
[COLOR=Navy]ls -ld /media/Data[/COLOR]
drwxrwxr-x 1 root *yournewgroup* 4096 2012-02-13 13:36 /media/Data
```Then people in that group should be able to write to the device, whereas people not in the group should have read-only access.

Try it and let us know if it works.

Thanks for your solution it worked perfectly! ;)

Im just confused why "mount" seems to show different to what is in /etc/fstab

```
/dev/sdb1 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

---

### Post by mcduck on 2012-02-14
> **moody_mark said:**
> Thanks for your solution it worked perfectly! ;)

Im just confused why "mount" seems to show different to what is in /etc/fstab

```
/dev/sdb1 on /media/Data type fuseblk (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
```

If you try to use options not suitable for the filesystem in question , the line in fstab will simply get ignored and the drive is mounted using your desktop environment's automatic mounting instead (therefore the type "fuseblk").

Also the "defaults" option simply means a set of default options, so "mount" will expand and show the actual options used instead of the "defaults". (for example my storage partition simply has "defaults" as it's options in fstab, and as the default options for Ext4 are "rw,commit=0", so those are what will actually be used and what "mount" will report)

---

### Post by Paddy Landau on 2012-02-15
> **moody_mark said:**
> Thanks for your solution it worked perfectly!
Excellent!

Please [mark the thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Morbius1 on 2012-02-15
> **fmask** and **dmask** are for FAT, not for NTFS (see the *mount* manual). You can use **umask** instead.I'm sorry but that is not correct. It's for NTFS as well. When you insert an NTFS external drive onto your system it mounts with all the files ( not folders ) set as non-executable. If does that internally by the use of the fmask/dmask option. Umask can't differentiate between a folder and a file so setting it to "0" will enable the execute bit on a folder ( which you must do ) but also on a file ( which you may not want to do ).

---

### Post by Paddy Landau on 2012-02-15
> **Morbius1 said:**
> I'm sorry but that is not correct. It's for NTFS as well.
Thanks for the information, Morbius. I got my information from mount's manual; perhaps mine is outdated (11.04)?

---

### Post by Morbius1 on 2012-02-15
You won't find the option "windows_names" in man mount either for ntfs. You need to go to the people who created the ntfs-3g driver: [http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/)

---

### Post by Paddy Landau on 2012-02-15
> **Morbius1 said:**
> You need to go to the people who created the ntfs-3g driver: [http://www.tuxera.com/community/ntfs-3g-manual/](http://www.tuxera.com/community/ntfs-3g-manual/)
That is useful, thank you.

---

