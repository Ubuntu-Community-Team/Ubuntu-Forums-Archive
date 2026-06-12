---
title: "Mark as executable - not working."
date: 2010-11-07
forum: General Help
---

### Post by TheNessus on 2010-11-07
Even as root when running Nautlis, it won't let me mark as executable, when the file in question is in a partition that is not /   - that is, on my win7 partition. I check the box, and it unchecks immedietly. It has no problem doing so when it's on /.

What do I do to make it happen?

thanks

ubuntu 10.10.

---

### Post by sikander3786 on 2010-11-07
> **TheNessus said:**
> Even as root when running Nautlis, it won't let me mark as executable, when the file in question is in a partition that is not /   - that is, on my win7 partition. I check the box, and it unchecks immedietly. It has no problem doing so when it's on /.

What do I do to make it happen?

thanks

ubuntu 10.10.
See in /etc/fstab if that mounted partition is having a **noexe**c flag.

```
cat /etc/fstab
```

---

### Post by TheNessus on 2010-11-07
$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda7 during installation
UUID=406858c4-857c-45a7-af3e-284878f88f8c /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda8 during installation
UUID=1fdfc8ba-3539-45d7-8bff-6f274abdd9b8 /home           ext4    defaults        0       2
# swap was on /dev/sda5 during installation
UUID=53dbc2d7-aa3e-4300-b537-50019713696e none            swap    sw              0       0


relevant partition not listed in this output...

---

### Post by Verbeck on 2010-11-07
try the command **mount**

---

### Post by mcduck on 2010-11-07
> **TheNessus said:**
> Even as root when running Nautlis, it won't let me mark as executable, when the file in question is in a partition that is not /   - that is, on my win7 partition. I check the box, and it unchecks immedietly. It has no problem doing so when it's on /.

What do I do to make it happen?

thanks

ubuntu 10.10.

You can't do that because the file is on a Windows partition. Windows filesystems, FAT and NTFS, lack the support for file ownerships and permissions as they are used in Linux/Unix systems.

Since the filesystem can't handle permissions, but Linux needs them, they are set for the whole partition at the time it's mounted. Like sikander3786 suggested, the solution to your problem is to check /etc/fstab and make sure the partition in question is configured there and has the "exec" option enabled. Or move the files to any Linux partition and run from there.

edit:
Two great guides to help you with fstab:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by TheNessus on 2010-11-07
> **Verbeck said:**
> try the command **mount**

erm... ofc it's mounted. I'm not an idiot, thank you. The output however does not list the NTFS partition in question (which is mounted, yes, really).

---

### Post by TheNessus on 2010-11-07
> **mcduck said:**
> You can't do that because the file is on a Windows partition. Windows filesystems, FAT and NTFS, lack the support for file ownerships and permissions as they are used in Linux/Unix systems.

Since the filesystem can't handle permissions, but Linux needs them, they are set for the whole partition at the time it's mounted. Like sikander3786 suggested, the solution to your problem is to check /etc/fstab and make sure the partition in question is configured there and has the "exec" option enabled. Or move the files to any Linux partition and run from there.

edit:
Two great guides to help you with fstab:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")
[http://ubuntuforums.org/showthread.php?t=283131]("http://ubuntuforums.org/showthread.php?t=283131")
Oh boy, that's a long one. Thanks, I'll give it a go.

---

### Post by Mark Phelps on 2010-11-07
Why are you trying to run executables from your Win7 partition in the first place?

If they're ".exe" files, they won't run in Linux because they're MS Windows executables, not Linux executables.  So, it doesn't matter how you mark them, they won't run in Linux.

You'll have to use Wine or something similar to run MS Windows executables in Linux -- and then, you should go to the WineHQ website first and check the compatibility of whichever app you're trying to run -- to see if it will even WORK in Wine.

---

### Post by TheNessus on 2010-11-07
> **Mark Phelps said:**
> Why are you trying to run executables from your Win7 partition in the first place?

If they're ".exe" files, they won't run in Linux because they're MS Windows executables, not Linux executables.  So, it doesn't matter how you mark them, they won't run in Linux.

You'll have to use Wine or something similar to run MS Windows executables in Linux -- and then, you should go to the WineHQ website first and check the compatibility of whichever app you're trying to run -- to see if it will even WORK in Wine.

Of course I did that. I installed Wine, winetricks, etc, all I need to use Starcraft II, which works according to WineHQ. Also to be able to use Evernote. Evernote works just fine albeit a bit slow, and SCII works badly since my IntelHD card is not working well with wine. I got it to work, obviously.

---

### Post by uksreejith on 2010-12-17
Even I am facing this problem.... this was not an issue in the previous versions of ubuntu...
but when i copied those files into the linux partition I was able to mark the file as executable...

---

