---
title: "fstab woes"
date: 2009-08-06
forum: General Help
---

### Post by ird on 2009-08-06
I found a thread with a similar problem to me, but the solutions didn't help.

I can mount the drives manually with sudo mount -a, but not automatically.

I have a 1tb external HDD with two partitions. One is NTFS with music, the other is fat32 with videos (since an xbox360 can't read NTFS for some odd reason.)

My fstab is as follows... (with the other drives removed for brevity)

UUID=663402D33AE7CD34 /media/music ntfs-3g rw,utf8,locale=en_US.utf8,umask=000    0       0
UUID=C819-2E90  /media/xbox vfat rw,umask=000              0       0

and fdisk -l

 Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       77095   619265556    7  HPFS/NTFS
/dev/sdc2           77096      121601   357494445    b  W95 FAT32

I get an error stating I don't have the privilege to mount the drive, but like above I can use sudo mount -a and they mount fine.

Any help would be very much appreciated. 

Thanks.

---

### Post by michy99 on 2009-08-06
When do you receive this error message? When you are booting up?

---

### Post by ird on 2009-08-06
It's an external drive, so whenever I plug it in I get the error.

---

### Post by dunkar70 on 2009-08-06
For enabling the drive during the bootup process, focus on the order in which your components start during the bootup process. Since you are talking about a USB drive, you need to make sure the USB functionality is available before you try to mount the drive. 

Do you need to have the drive accessible before you log in? The easiest solution is probably to have a login script that executes the mount command as you log in.

Now that I've typed that, I noticed you're referring to plugging the drive in after you log in. Add ",users" to the fstab file after the rw statement. Your lines would look like this...

> UUID=663402D33AE7CD34 /media/music ntfs-3g rw,***users***,utf8,locale=en_US.utf8,umask=000 0 0
UUID=C819-2E90 /media/xbox vfat rw,***users***,umask=000 0 0

---

### Post by Hobgoblin on 2009-08-06
> **ird said:**
> It's an external drive, so whenever I plug it in I get the error.

System > Administration > Users and groups

unlock

select your user, then properties

click the user privileges tab

Check "access external storage devices automatically" is checked.

[edit]
ah, I see you have them in fstab.

You will need user adding to the options.

I'm guessing.....
```
UUID=663402D33AE7CD34 /media/music ntfs-3g rw,utf8,user,locale=en_US.utf8,umask=000 0 0
UUID=C819-2E90 /media/xbox vfat rw,user,umask=000 0 0
```

---

### Post by ird on 2009-08-07
Thanks, I'll try this out when I get home.

---

