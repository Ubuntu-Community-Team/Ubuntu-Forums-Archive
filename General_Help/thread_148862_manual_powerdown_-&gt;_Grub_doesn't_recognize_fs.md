---
title: "manual powerdown -&gt; Grub doesn't recognize fs"
date: 2006-03-22
forum: General Help
---

### Post by GooglePlexity on 2006-03-22
I was using Ubuntu (Breezy) and it crashed (a rare occurence) so I had to manually turn the power off using the power button on my computer.

But then the next time I turned on my computer, nothing booted: the manufacturer's screen just stayed there. I was able to get it to the point where it got to the boot screen, but after boot from CD was displayed it didn't show GRUB, which I fugred out to be because my second NTFS hard drive had somehow become an active, bootable druve,

So anyway, once I got that fixed, it now says Grub loading, please wait... Error 17, which is when the partition exists but the file system can't be read.

So did my manually powering off Ubuntu somehow cause the file system to be wreck, by not unmounting it or something? I am a complete linux noob and I need help! I tried using my various rescue disks. PartitionMagic says the file system is Ext2, and Acronis says the type is Linux Extended, but the filesystem is "None," and I can't seem to be able to change it. They also indicate that there is no free space in the partition.

When I use the Ubuntu Live CD, it recognizes the Drive and Partition but not the filesystem (it says "Unformatted"). Is there any way to make it work? I don't think I have a problem with grub or the mbr or whatever, just the filesystem not being right. I need some of my files on the Ubuntu, and I need to preserve the Windows installation too. Right now, if I could just boot either, that would be great. Oh, and if you have any suggestions, could you spell them out for me, because as I said I'm a complete linux noob. Thanks.

---

### Post by dragomirov on 2006-03-22
It seems that your partition is corrupted and you've lost it. It happens seldom when you turn off brutally yr computer when some writing process occurs. Unlucky you.

So, if you had any important data on that partition cross your finger and look for some software to try to rescue them.

---

### Post by GooglePlexity on 2006-03-23
I guess I can deal with that.  Do you recommend any programs?  Ones I can run from a CD, because I can't boot into Ubuntu or Windows.  Oh, and if I format that partition, will Grub still be installed and if it is how do I uninstall it?

---

