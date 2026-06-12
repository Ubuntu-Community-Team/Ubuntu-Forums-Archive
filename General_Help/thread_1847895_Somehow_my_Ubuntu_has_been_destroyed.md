---
title: "Somehow my Ubuntu has been destroyed?"
date: 2011-09-21
forum: General Help
---

### Post by RonB123123 on 2011-09-21
I left my laptop in hibernation mode and took off the battery which is a big mistake. The next day I plugged the battery back in and tried to load Ubuntu and it said something like "error mounting '0' drive" or something.

It also said hit S to skip or M to manually mount so I kept hitting S to get into the OS. When I finally got in, everything seemed to work fine except for the wireless internet. I restarted the computer and it did the same thing so this time I hit M to manually mount. I gave it my root password and I typed in "fsck" and then it displayed:

Continuing will cause SEVERE DAMAGE to your computer.

I wasn't paying attention at 6 in the morning and typed in Y. After reading it, I panicked and shutoff my laptop.

Now I boot my laptop and it displays:

error: unknown filesystem
grub rescue>

And it gives me a grub error prompt. I put in my gparted USB stick and when it booted, GParted said the partition that I normally use is now "Unknown" instead of it saying "Ext4"

So is there a way to fix this problem? If not, are all my files corrupted or are they recoverable?

Thank you very much,
Ron

---

### Post by seawolf167 on 2011-09-21
I would stop everything and immediately make a backup image of your computer with [Clonezilla]("http://www.clonezilla.org"), then attempt to use [TestDisk ]("http://www.cgsecurity.org/wiki/TestDisk")(guide [here]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step"), download [here]("http://www.cgsecurity.org/wiki/TestDisk_Download"), live cd list [here]("http://www.cgsecurity.org/wiki/TestDisk_Livecd")) to see if you can recover your partition.

If you can recover your partition/data, you can restore Grub2 following this [guide]("https://help.ubuntu.com/community/Grub2/#Reinstalling_GRUB2").

As a side note: you can never have too many backups!

---

### Post by MG&amp;TL on 2011-09-21
...I thought 

```
fsck
```
stood for filesystem check? Because that's what I would have done...:shock:

EDIT: or not, it seems you can't do it while it's mounted. :confused:

---

### Post by seawolf167 on 2011-09-21
Check **and** repair - the corrective actions could result in the loss of data from the filesystem, **especially** if mounted.

---

