---
title: "Partition issues (seriously messed up this one)"
date: 2010-09-07
forum: General Help
---

### Post by Randomwolf42 on 2010-09-07
Okay, this is an issue that I've had for a while, and I've looked around everywhere, but nobody seems to have an answer to my particular problem.

When I installed Ubuntu originally, I had two partitions on Windows XP already, C and D (D was 'unformatted', according to Windows). My plan had been to install Ubuntu on the D drive and there wouldn't be a problem (my harddrive was split roughly in half), but as soon as I got to actually installing it, I instead installed it using the space from my C drive, and giving Ubuntu way more room than it would ever need.

Well, now I'm left with a 14.5 or so GB windows partition (with only about 1 GB remaining) that I need to boot in all the time (because my USB wifi thingy isn't supported by Ubuntu, but that's a problem for another day). I've read a lot about resizing partitions, but those are mostly for making the Ubuntu partition bigger. I have a CD with a more recent version of Ubuntu now, so I'm thinking I'm going to have to delete the partition, because I used the live CD to make the Ubuntu partition smaller, but I ended up cancelling it and I haven't tried booting into it since, I think it might be corrupted (most likely it is). Either way, I found it shows a bunch of unallocated space, but it won't let me expand my Windows partition with that space, is there any way to do this without reformatting, or am I out of luck?

---

### Post by srs5694 on 2010-09-07
If the unallocated space is contiguous with the Windows partition, try using the Windows disk utility to expand the Windows partition. If that won't help, try posting the output of "fdisk -lu" or a screen shot from GParted; that will give us a clearer idea of how your disk is currently partitioned.

---

### Post by Randomwolf42 on 2010-09-08
Okay, so GParted won't do it on its own then? I know I need to move the Ubuntu partition, because from what I can tell, the unallocated space is between Ubuntu and it's swap partition, but it takes me forever to do that, either way. I was wondering if it might not make more sense to delete the Ubuntu partition entirely, fix the Windows one, and try a fresh install of Ubuntu, and then work on my wifi issue after?

---

### Post by Mark Phelps on 2010-09-08
It's hard for us to give detailed advice if you won't follow our directions ...

You were asked to post the output of "sudo fdisk -lu" or a GParted screenshot.

Until we see those, we are guessing and likely to give you BAD information.

---

### Post by Randomwolf42 on 2010-09-09
Okay, here's the screenshot from GParted. I don't know if this makes my rambling make any more sense, but hopefully you can see what my problem is. (As you can see, I already tried to shrink down the Ubuntu partition, and I *think* it worked.

---

### Post by sxmaxchine on 2010-09-09
I think you are in a little bit of a pickle however all i can suggest is to uninstall ubuntu increas the size of windows partition and then reinstall ubuntu with the unused space.

hope this helps.

---

### Post by srs5694 on 2010-09-09
Here's one possible solution:


[list=1]
[*]Back up Windows using Windows-native tools.
[*]Back up Linux using Linux-native tools.
[*]Boot a Linux emergency disc. The Ubuntu install disc in "live CD" mode might work, or you could use [PartedMagic](http://www.gnu.org/software/parted/) or [System Rescue CD.](http://www.sysresccd.org/)
[*]In the emergency disc environment, locate and launch GParted.
[*]Using GParted, move the Linux partition all the way to the right. (You can also optionally resize it.) This operation is likely to take a while -- perhaps a few minutes, or maybe several hours. This action will free up space that's contiguous with the Windows boot partition; however, it still won't be quite accessible until you do the next thing....
[*]In GParted, resize /dev/sda2, the extended partition, so that its left side starts later. This will move the free space at the start of /dev/sda2 outside of it, making it accessible to /dev/sda1, your Windows boot partition.
[*]Reboot into Windows.
[*]Use the Windows disk utility to resize the Windows boot partition. This operation will probably take less time than the Linux resize/move operation.
[/list]


Steps #1 and #2 are optional; but if you don't perform these steps and something goes wrong, you'll lose your data. Resizing and moving partitions are inherently risky operations, so you shouldn't do them without backups unless you don't care about the data.

It's possible to resize the Windows partition using GParted instead of Windows; however, the Windows tools have a reputation for being a bit safer at NTFS resizing than GParted is. It should also be possible to resize the extended partition in Windows, if GParted gives you trouble with this; however, I'm only passingly familiar with the Windows partitioning tool, so I'm not positive of this.

It's possible you'll have problems booting Linux after you move/resize it. If so, you can use [Super GRUB Disk](http://www.supergrubdisk.org) or the Ubuntu installer to restore the OS to bootability.

If you don't have important data and haven't spent much time customizing the Ubuntu installation, it might be quicker to delete the Ubuntu partition, resize /dev/sda2, resize /dev/sda1, and then re-install Ubuntu than to try to move the existing Ubuntu installation.

---

### Post by Randomwolf42 on 2010-09-12
On the one hand, it worked, but on the other hand it gave me an error at one point to the effect that my harddrive was failing anyway, it 'has many bad sectors', so I'm going to have to redo it all anyway. The expansion worked though, and that's what my question was, so Thanks! I'm backing everything up now, I have no idea how much longer I'll have...

---

