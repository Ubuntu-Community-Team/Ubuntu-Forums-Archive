---
title: "Utility for creating a mount point"
date: 2012-10-10
forum: General Help
---

### Post by pwabrahams on 2012-10-10
Is there a utility around for creating a mount point for a partition?  I know quite well how to create a mount point by editing **/etc/fstab**, but that's not as clean as using a utility with that capability -- especially since it's possible to create such mount points during system setup.  I thought that gparted or the KDE partition editor would have the capability, but they don't.

---

### Post by twipley on 2012-10-10
The "Disk Utility" of quantal has been revamped, although I cannot remember if it features such an option. (v3.6.0+)

Otherwise, I am not sure what could I suggest.

---

### Post by oldfred on 2012-10-10
There are three older gui tools that I know, but all have not been well maintained and do not always put in good parameters. PYSDM, Storage Device Manager &  NTFS Config (obsolete). 

I have the same data partitions whose UUIDs do not change so I just script the update as part of my new install. But I am installing every new version at least twice, even if still using an older version as my main install, so it was worthwhile to script it.

[http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
suggest using templates instead. Post #6

---

### Post by pwabrahams on 2012-10-10
I tried installing **pysdm**.  It seems to work, more or less, but I immediately encountered a bug: it thought that sda10 was a different drive.  But it handled sda9 correctly.

---

### Post by dcstar on 2012-10-11
> **pwabrahams said:**
> Is there a utility around for creating a mount point for a partition?
........

A "Mount point" is simply a folder in a filesystem which can be created thus:

```
sudo mkdir /path/to/mountpoint
```

Once the mountpoint exists **then** fstab can use it to mount a device.

---

### Post by pwabrahams on 2012-10-11
I should have been clearer, since I certainly know how to do this stuff with an editor and **mkdir**.  The two steps I've always gone through are:

1. Create a directory that will serve as a mount point using **mkdir**.

2. Using the editor (as root), add a line for the additional partition to **etc/fstab**.

Incidentally, I found it very useful to include among my systems programs "root kate".  That's a version of the **kate** editor that runs as root.

The **pysdm** program works very nicely -- provided that you don't need to handle any partitions beyond **sda9**.;)

---

