---
title: "Windows partition not viewable in Linux"
date: 2009-09-05
forum: General Help
---

### Post by Sim-I-Am :} on 2009-09-05
Hey all, I recently converted my Uncle over to Ubuntu Linux (From XP); He's a moderate user, and is going to be using it mostly for surfing the net, but will also be running navigational software for his sailing excursions. 
He's really enjoying it, but just recently His dual-booted windowsXP partition disappeared from the 'Places' list, and is only viewable in GPartEd. He's tried using the 'mount' command, manually typing the directory into nautilus (i.e. /media/mydrive/), and opening it via GpartEd, but nothing has worked yet. His external (FAT32) HD shows up fine, along with all other drives.

Any help would be appreciated

Thanks,
~Sim-I-Am


Note: I don't know if this would affect anything, but Windows and GPartED seem to think that the delinquent drive is formatted as FAT32. :confused:

---

### Post by Sim-I-Am :} on 2009-09-07
bumpety bump

---

### Post by PeEllAvaj on 2009-09-07
It's possible the hard drive has gone bad.  You could try mounting with "mount.ntfs-3g" (same thing as "mount -tntfs-3g") which will only mount drives as NTFS.  You could also try unplugging the drive, plugging it back in, and checking your hardware log with "dmesg" or "lshw", this will show you what linux can see.

---

### Post by Sim-I-Am :} on 2009-09-07
If the drive is bad, then why would it still show up in windows?

---

### Post by MelDJ on 2009-09-07
did you try looking in the mnt and media folder is filesystem?

---

### Post by nix85 on 2009-09-07
Does he hibernate in windows? If yes, then the partitions will not show up in ubuntu. It is a precautionary measure.

If he hasnt hibernated, then can you please paste the output of

```
$ sudo cat /etc/fstab
```

---

### Post by TheStickyNoteKing on 2009-09-07
There are a few things that might have happened... He might have accidentally removed the necessary drivers, so you should check that ntfs drivers have been installed in synaptic.

Next, the folder that the drive should be mounted on has disappeared. Check /etc/fstab to see where it is supposed to mount, and then check that the folder is actually there. If not, create it.

If windows did not shut down properly last time it was used, the partition probably didn't unmount properly either, and you need to run a chkdsk from windows.

Also, it would be helpful if you could describe what you mean by "but nothing has worked yet." That is, what does the terminal say when you try to mount the partition manually?

---

