---
title: "formatting ext. HD as HFS+ but have permission problem"
date: 2011-05-03
forum: General Help
---

### Post by carbon512 on 2011-05-03
I have done quite a bit of searching on the many threads about this but am perplexed.

Got a new 550GB external drive. Want to format it so my OSX box and my Ubuntu Maverick netbook can both have rw access. I'll live without Windows rw ability, and I do need to put on some LARGE video files. So I figured HFS+ unjournaled was best for me, don't want to use FAT.. also would rather not have to install anything to make the Mac read ex2 or a variation of that, since I use this on lots of different Macs.

Formatted it as HFS+ unjournaled on the Mac -- Ubuntu netbook sees it but will not write to it, permission problem (I am using Nautilus GUI because I still am not fluent in terminal commands at all)

If I run nautilus as root, I can write to the drive. But that is not a very good workaround -- kind of a PITA...

what am I missing to be able to just mount this drive and write to it as a user? HOw can I change the permission on the drive? (If that is what I need to do)

I don't really need partitions on it but could do that if needed (already tried two partitions: one GUID partition and one MBR partition but they behaved the same way)

Thanks --

---

### Post by coffeecat on 2011-05-03
Just chmod it with 777 permissions. This is what I've done with my non-journalled HFS+ external drive used to transfer files between Ubuntu and MacOS and it works just fine. You don't have to do a recursive chmod. Just chmod the root of the filesystem and the chmod sticks for both OSs. In fact you have a choice of which OS to use for this! :)

Ubuntu:

```
sudo chmod 777 /media/mountpoint
```MacOS:

```
sudo chmod 777 /Volumes/mountpoint
```Just substitute whatever mountpoint is in use in the above commands. run 'ls /media' in Ubuntu or 'ls /Volumes' in MacOS to find out what this is.

**EDIT**: just in case someone chips in. Those commands chmod the root of the filesystem, not the mountpoint itself. This is why it sticks. This is a subtle but not widely understood point.

---

### Post by carbon512 on 2011-05-03
thanks!
I had actually just come back here to do a quick "delete my post because I can't believe I was so stupid" because I realized I could do exactly the same thing in the OSX GUI by simply changing permissions on the drive to allow "everyone" to have "read/write" access.

But now I know the cooler way to do it, too...

---

