---
title: "drives mounted to different devices on startup"
date: 2010-04-30
forum: General Help
---

### Post by ants280 on 2010-04-30
My computer has three drives: one with windows7,one as a storage drive, and an ide drive.  I have ubuntu 10.04 installed on a seperate partition on the storage drive (+swap partition).  I have "/etc/fstab" automatically monut these drives on startup:
```

/dev/sdc1 /media/win7           ntfs-3g quiet,defaults,rw 0 0
/dev/sdb1 /media/storage        ntfs-3g quiet,defaults,rw 0 0
/dev/sda1 /media/ide            ntfs-3g quiet,defaults,rw 0 0

```
I have these folders created in /media.  The problem sometimes occurs when I reboot my computer.  The partitions (/dev/sb[a-c]1) are assigned to different drives.  As an example, right now drive folders are { sda1=>storage, sdb1=>win7, sdc1=>ide }.  This problem did not occur when I had 9.10 installed on the same partition (I just did a clean install).

BTW, I used this guide (karmic for 9.10) for the fstab setup: [http://ubuntuguide.org/wiki/Ubuntu:Lucid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29 ]("http://ubuntuguide.org/wiki/Ubuntu:Lucid#Mounting_NTFS_Partitions_.28with_read.2Fwrite_privileges.29")

---

### Post by ajgreeny on 2010-04-30
I am not sure I quite follow what the problem is, but you could use tune2fs to give labels to the partitions then they will always mount to a folder with the partition label name.

If I have got the wrong problem from your description, come back again and I'll see if I can help.

---

### Post by Morbius1 on 2010-04-30
I had to look up the "quiet" option in man mount:
> 
[B]quiet
[/B]Turn on the *quiet* flag. Attempts to chown or chmod files do not return errors, although they fail. Use with caution!And that was under the subheading for FAT32 not NTFS. Since you can't chmod or chown an NTFS or FAT32 filesystem anyway I don't know why it's there.The "rw" option is redundant - it's in "defaults" - but it won't harm anything. ntfs-3g really isn't needed anymore either - but I'm just getting picky. 

Sorry, it's just that I'm always surprised at these HowTo sites. To get back to your original problem, run the following command to see how the system sees these partitions at this moment:

**sudo blkid -c /dev/null**

---

### Post by StuartN on 2010-04-30
> **ants280 said:**
> This problem did not occur when I had 9.10 installed on the same partition (I just did a clean install).

Why is this a problem for you? (I mean that sincerely, not argumentatively). Presumably you can refer by label and never need to use device, and should not rely on device numbering.

I understand that this is causing some problems with raid, where device number is used as a reference and changes between boots.

---

### Post by ants280 on 2010-04-30
I fixed it!!! The problem was My UUID's were just copied over from thee previous install (they're UNIQUE!!!--they change!!!)

I switched the root and swap partition's UUIDs and that didn't fix it, so then I tried the ntfs drive's.  I referenced them by UUID instead of /dev/sd*.  that did the trick. (I've rebooted 3 times)

The "sudo blkid -c /dev/null" command greatly helped identify the UUIDs.

---

