---
title: "Trying to access my Vista files via Ubuntu"
date: 2009-08-03
forum: General Help
---

### Post by New2Linux13 on 2009-08-03
I have been unable to access my files on Windows Vista (the OS is stuck in a, "configuring updates" loop). I am using my Ubuntu Live CD to boot the sick computer, and using the two DVD drives (one which is DVD RW), I want to see my Vista files (I do know that they are still there) and burn the data with an Unbuntu burning program. So far, I have been unable to that.

/dev/sda3 is the location of my HPFS/NTFS. Upon using 
sudo mount /dev/sda3 /mnt/windows -t ntfs -o umask=0002,nls=utf8 
I receive the following message:

NTFS signature is missing.
Failed to mount '/dev/sda3': Invalid argument
The device '/dev/sda3' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?

Using mount -t ntfs-3g /dev/sda3 /mnt/windows has the same result.

What should I do now? Thank you.

---

### Post by Codix121 on 2009-08-03
I would go to PLACES > COMPUTER > and look for the name of your Windows Harddrive....
and you should be able to access them?
I use to do it all the time,
or your harddrive might be corrupt and it why the file aren't coming up.

---

### Post by New2Linux13 on 2009-08-03
> **Codix121 said:**
> I would go to PLACES > COMPUTER > and look for the name of your Windows Harddrive....
and you should be able to access them?
I use to do it all the time,
or your harddrive might be corrupt and it why the file aren't coming up.

The name of my Windows Harddrive is not there. I think I should also note that I have *never* been able to see it in that section, even when I was able to access the drive via the Vista OS...

---

