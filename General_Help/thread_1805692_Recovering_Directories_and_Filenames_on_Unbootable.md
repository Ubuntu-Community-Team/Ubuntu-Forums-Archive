---
title: "Recovering Directories and Filenames on Unbootable Partition"
date: 2011-07-16
forum: General Help
---

### Post by markekeller on 2011-07-16
I had my /home and /usr/local directories as XFS partitions on a separate disk from my main Linux installation, and one day the disk simply stopped working. Because I've got no /home I can't boot, but that's not really the problem for me. I mostly just want my data back!

I ran Testdisk on the drive and everything appeared to work right, but it still won't boot. So I tried Photorec, but of course that program only takes file data and ignores filenames and directory structure. After about 13,000 files I realized this wasn't going to work. Having my files randomly strewn in with my Firefox history and the code from several projects I'd downloaded is hardly better than not having them at all.

So, my question: is there anything else I can do? I'll take either fixing my partitions or recovering my data intact with filenames and directories as a success. :D

---

### Post by DawieS on 2011-07-16
If I understand you correctly, the disk with your your home folder (containing all your data) seem to work right, but you are not able to boot from your (other) main Linux disk, and you need to backup your data urgently.

I recommend that you:
- adjust the boot sequence in the BIOS to boot from CD (or USB HDD).
- boot from a Live CD (or USB thumb drive), and choose "Try Ubuntu" when it boots up. Then click on **System > Administration > Disk Utility**. Look if you can see your data disk, then run **Check Filesystem** on all your partitions.
- If all checks clean, connect a USB disk and proceed with your backups. You can repair your Ubuntu installation later.

---

### Post by markekeller on 2011-07-19
Mmm, no, I must not have been clear. You've got it backwards — my main Linux disk works fine; in fact, I've got it dual-partitioned with Windows XP which I'm running right now. My home disk is what's having problems. The BIOS doesn't even recognize it, but Testdisk and Photorec don't seem to see any problems with it. The reason I can't boot Linux is because it needs a /home directory, which it can't find.

What I'm looking for is an alternate way to fix my filesystem/recover my files that keeps filenames and directory tree intact.

---

### Post by DawieS on 2011-07-19
Uhmm, now that is a difficult situation. AFAIK, if the BIOS does not even see the disk connected, then no software or OS will be able to repair or rescue any data on that disk from that machine, and you would not have been able to see it with Testdisk and Photorec.

A while ago I helped a friend whose disk has failed. The disk was seen by the BIOS once in about five re-boots, and quickly got worse. It would then go off-line while copying from it. In this way we managed to get about half the data off, sometimes doing a complete shut-down and disconnecting the disk, then trying again.

I then installed the disk in an external enclosure and was able to get the rest of the data off via USB. It was also quicker to restart the disk, than a complete reboot, whenever the disk went off-line.

Normally it is electronic components on the controller card of the disk that fails with an increase in temperature. I have heard of instances where it has helped to put the disk in a freezer for a while, then it would work for another half an hour or so.
> **markekeller said:**
> The reason I can't boot Linux is because it needs a /home directory, which it can't find.
The Live CD does not require the presence of a /home folder. I recommend that you boot from a Live CD, and repair the file systems as per my previous post, if the Disk Utility is able to see the disk. Also check the SMART status of the disk.

If you manage to get the file systems repaired, do not try to copy off all at once, rather take it in chunks, starting with your MOST valuable data. You may not be able to get it all off.

If all else fails, you also have the option to take the disk to a data recovery specialist, who will install the platter in another working drive frame under sterile conditions. It will cost you an arm and a leg, and there is no guarantee of a 100% recovery, especially if there was mechanical failure that damaged the disk surface.

Good luck!

---

### Post by markekeller on 2011-07-21
Alright, so I ran Gnome Disk Utility from a live CD. The drive and its partitions came back as clean, but when I tried mounting one, I got this:

```
Error mounting: mount: /dev/sdb1: can't read superblock
```

The Disk Utility SMART check returned clean as well, but GSmartControl's more thorough check gave me errors. A full log of which can be found [here]("http://pastebin.com/57cAkEJx") in case anyone wants to read it. It returned a soft-read error rate of 3 (odd, since Disk Utility said it was 0) and recommended that I should back up my data because of risk of future failure. Which is already what I was trying to do, ha!

Is there any way I can mount this drive aside from freezing the thing or taking it to the recovery pros?

---

### Post by DawieS on 2011-07-22
I recommend that you:
1) disconnect the disk in question to prevent any possible further damage.
2) create a fully functional Ubuntu installation, possibly on an external disk. It is good practice to have at least one extra copy on a small partition, for maintenance and troubleshooting purposes.
3) boot from this installation, and install **xfsprogs** in **Synaptic Package Manager**. This will install a set of tools, to be used with the XFS filesystem.
4) reconnect the failing disk and run the tools **xfs_check** and **xfs_repair** on all XFS partitions on the disk.

I don't know a thing about XFS filesystems, and would not be able to help you with that. You may want to read up some documentation on [http://oss.sgi.com/projects/xfs/](http://oss.sgi.com/projects/xfs/) if you need help with the repair.

I hope you are able to repair the XFS filesystems, after which you may copy off your data.

Good luck!

---

### Post by markekeller on 2011-07-22
Hmm, this looks grim. I tried running the XFS tools, and got the following:

```
ubuntu@ubuntu:~$ sudo xfs_repair /dev/sdb1
Phase 1 - find and verify superblock...
bad primary superblock - bad magic number !!!

attempting to find secondary superblock...
...................
```
And then it filled the screen with periods until I realized it wasn't going to find anything and stopped it. So I went on:
```
ubuntu@ubuntu:~$ sudo xfs_check /dev/sdb1
xfs_check: /dev/sdb1 is not a valid XFS filesystem (unexpected SB magic number 0xeb52904e)
xfs_check: size check failed
xfs_check: WARNING - filesystem uses v1 dirs,limited functionality provided.
Segmentation fault (core dumped)
```
Any XFS-knowledgeable types out there who feel like giving me a hand? This looks fairly hopeless to me, but I don't really know.

---

