---
title: "External HDD automount"
date: 2009-11-06
forum: General Help
---

### Post by Replicasex on 2009-11-06
I've seen several threads in a similar vein here but none that fully answered my question -- I apologize if this feels like an oft repeated question.  

I have been using Ubuntu for little under 2 years and have been very happy with it.  I'd describe myself as a moderately experience computer user but I just recently switched to Kubuntu (to give it a whirl) for my upgrade to 9.10.  

My only annoyance with it is the fact that my external terabyte drive is not mounted on the desktop when I log in -- I can go into the file manager and click on the drive and it will show me my files just fine.  But I was wondering if there was a way to have that hard drive (and perhaps my internal windows partition with the rest of my data) to automount when I log in?  

It's not a huge problem as I can get to my data just fine but I would really appreciate it if I had them already mounted (at the very least my external)  Now I know I can right click the drive in the 'computer' part of the k menu and have it display as a file folder on the desktop but every time I reboot it no longer works, I suppose it is no longer mounted there.  

Can anyone give me a step by step guide (if it's possible) to set these drives up for automount?

---

### Post by coffeecat on 2009-11-06
You can have both your external drive and your internal Windows partition automounted when you boot up by means of editing your /etc/fstab file. This guide will get you started:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

One caveat - when you say Windows partition, is that XP or Vista? Although Ubuntu can read and write to NTFS filesystems quite reliably, Vista doesn't like it if something has been writing to its C: drive while it's not been looking. In fact it's been known to go into a massive sulk and refuse to boot up. XP doesn't have this problem as far as I know, unless you do something unwise such as mess around in the Windows folder. :)

By all means mount a Vista partition but I would be chary about writing to it. That being said, so far I haven't had a fit of the vapours from Vista after I've written to a shared NTFS Data partition. And I would guess W7 is as fussy as Vista.

---

### Post by Giblet5 on 2009-11-06
Put entries in /etc/fstab for them.

Do the internal windows drive using the device

Example: ```
sudo mkdir /media/CDrive /media/External
sudo chmod 777 /media/CDrive /media/External
```

Now go find the UUID for that external drive: ```
ls -l /dev/disk/by-uuid
```

Select and copy the UUID for that external drive.

Then make fstab entries: ```
/dev/sda1 /media/CDrive ntfs nls=utf8,user,auto,exec 0 0 1
UUID=[COLOR="Orange"]xxxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxx[/COLOR]  /media/External  ntfs  nls=utf8,user,auto,exec  0  0  1
```

Where the xxxxx are the uuid you copied above.

---

### Post by Replicasex on 2009-11-06
I do mean a Win7 partition.  But I'm not *too* worried as I very rarely write to it (as in create or edit files within windows).  I usually use my external more than the actual partition, I honestly just want it to be there so i can get my music to play in amaroc without copying all of it.  

I'll look into the guide some more.  the general gist is that I have to edit the /fstab/ right?  But what code do I add to make my drive automount?  fdisk -l shows this for my external.  

```
Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8900690

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121601   976760001    c  W95 FAT32 (LBA)

```

I already have a folder /media/elements (the hard drive) so I'm not sure I would have to mkdir anything.  Do I basically just add the file path (plus the other variables there).  I think it would look like 

```
/dev/sdb1   /media/elements   vfat   user,fmask=0111,dmask=0000   0   0
```

Does that look good?

---

### Post by Replicasex on 2009-11-06
Giblet5, thanks for the information.  

The output from ls -l /dev/disk/by-uuid is:

```
total 0
lrwxrwxrwx 1 root root 10 2009-11-06 05:44 52e4d31e-817b-4527-9fbe-fbaee05eab9e -> ../../sda2
lrwxrwxrwx 1 root root 10 2009-11-06 05:44 7c67d3ca-3035-4fe3-aab1-c1b31f60cb0c -> ../../sda5
lrwxrwxrwx 1 root root 10 2009-11-06 10:44 DE1E-BC06 -> ../../sdb1
lrwxrwxrwx 1 root root 10 2009-11-06 05:44 EE08065608061DE9 -> ../../sda1

```

/sbd1 was what I think my external is (that's what it showed up as when I checked it with fdisk).  Is the UUID  DE1E-BC06?  That seem a lot shorter than the field you had written.  Sorry if I'm a n00b, I've never played around with this part of linux before.  

And do I explicitly need to mkdir those directories if I already have entires like /media/elements and so forth?

---

### Post by coffeecat on 2009-11-06
> **Replicasex said:**
> ```
/dev/sdb1   /media/elements   vfat   user,fmask=0111,dmask=0000   0   0
```Does that look good?

It's a long time since I've had to add a vfat drive to fstab but that line is consistent with that link's "more permissive" options, so it should be OK. 

> I advise dmask=027,fmask=137 (if you user umask=000 all your files will be executable). More permissive options would be dmask=000,fmask=111.I notice there's a "default" at the beginning of the fourth field in the examples in the link, although I would have thought you'll be safe without it.

Before you use it in anger, do a few drag and drop copies each way to/from your Ubuntu root partition. Over the years NTFS and VFAT mounts have had a habit of changing the date/time on copy depending on the fstab mount options. It's caught me out on more than one occasion.

One thing to think about. A 1TB HD formatted to FAT32? Hmmm. I know you've probably got a whole load of stuff on there already, and you have to use it with Windows, but have you thought about re-formatting it as NTFS? With journalling, NTFS is more robust and permits filesizes greater than 4GB. And you've got Windows to do a chkdsk if the FS gets corrupted. You're much more likely to lose data with FAT32.

---

