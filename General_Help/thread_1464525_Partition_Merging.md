---
title: "Partition Merging"
date: 2010-04-28
forum: General Help
---

### Post by mc_tux on 2010-04-28
Hello,

here's a screenshot of what my GParted shows:

[IMG]http://www.ipix.lt/images/84105835.png[/IMG]

The problem: I want to merge the empty partition named PARAGON with the right one - /dev/sda8, as I need more space on that /dev/sda8 partition. Is it possible to do that? When I try to resize/move any of these two partitions, GParted doesn't let me increase the size. Is it a problem that they're not next to each other?

---

### Post by mikewhatever on 2010-04-28
Well, as you can see, there is no unallocated space to 'increase' to. As for merging, sda5 and sda8 are not next to each other, and you'll have to move sda6 and sda7 out of the way before merging.

---

### Post by srs5694 on 2010-04-28
As mikewhatever says, you'll need to delete /dev/sda5 and move two partitions to add that space to /dev/sda8. Both /dev/sda6 and /dev/sda7 are currently in use, though, and GParted won't let you operate on in-use partitions. If you're booting from /dev/sda6, you'll need to use an emergency disc to do the work. Unfortunately, move operations like this are among the riskiest you can perform with GParted. Given the number of operations, I'd be a bit wary of this, and I wouldn't recommend doing it at all unless you've got good backups of all your logical partitions (aside from your swap space) and/or you don't care about losing the data. If you *do* embark on this journey, I'd recommend consolidating your two swap partitions into one while you're at it.

Another option would be to use the free space as another partition (as it is now, in fact). Under Linux, you could mount /dev/sda5 somewhere within /dev/sda8's directory, if you like. For instance, if you mount /dev/sda8 at /mnt/somewhere, you could create a directory called /mnt/somewhere/morestuff and mount /dev/sda5 there. This will at least present all your files as being within a single directory tree, although you'd have limits about how much stuff you could put where. I believe that Windows has a similar feature, although I don't know much about it.

---

### Post by dino99 on 2010-04-28
> **mc_tux said:**
> Hello,

here's a screenshot of what my GParted shows:

[IMG]http://www.ipix.lt/images/84105835.png[/IMG]

The problem: I want to merge the empty partition named PARAGON with the right one - /dev/sda8, as I need more space on that /dev/sda8 partition. Is it possible to do that? When I try to resize/move any of these two partitions, GParted doesn't let me increase the size. Is it a problem that they're not next to each other?

you need to make room, your disk is over loaded :rolleyes:

install with synaptic: bleachbit and use it with care (dont erase bookmarks, passwords, ...), then remove the first swap and your paragon partition then resize the extended partition first. then move and resize the one you need.

note: use gparted or better partedmagic from a cd or usb on which you boot (never on a active partition)

---

### Post by mmcmonster on 2010-04-28
Warning:  This is a potentially very risky thing to do.  Moving partitions is risky under any OS, at any time.  Back up all information from the computer, accordingly.

You'll have to boot off a CD.  You should probably download the [gparted Live CD]("http://gparted.sourceforge.net/index.php") and use that.

1.  Delete /dev/sda5
2. Move /dev/sda6 to the left
3. Move /dev/sda7 to the left (or delete it)
4. Resize /dev/sda8.

Also realize that the partitions will likely change names (/dev/sda6 will become sda5) after a reboot, so you'll have to change your fstab file or reinstall the OS. (Could be a good time to do some cleaning, with Ubuntu 10.04 coming out in a couple days. :-) )

As an aside, I'm not sure why you have two swap partitions.  Especially with both of them > 1GB.  Are you even using swap space much?  I use my computer fairly heavily and only have 1GB swap and rarely even touch it, according to system monitor.  Guess you'll need more if you have little ram and run some seriously hungry apps.

Another aside:  You have a fat32 partition.  Presumaby this is to share data between Windows and Ubuntu, since you are apparently dual booting this computer.  My impression was that Ubuntu's ntfs write was rock solid at this point.  If this is so, you may want to consider changing this to an ntfs partition.  Providing you can back up the data, of course. :-)

---

### Post by mikewhatever on 2010-04-28
> **dino99 said:**
> you need to make room, your disk is over loaded :rolleyes:

install with synaptic: bleachbit and use it with care (dont erase bookmarks, passwords, ...), then remove the first swap and your paragon partition then resize the extended partition first. then move and resize the one you need.
...

Bleachbit will probably only act on the Linux system partition, sda6, which has quite a lot of free space, which makes it kind of pointless, especially since you also suggested removing it. Why not just delete it and skip bleachbit?'

---

### Post by psusi on 2010-04-28
In order to do it, you need to delete sda 5, 7, and 9, then move sda6 to the left, then recreate the swap partition ( you should only have one ) then move sda8 to the left, then finally extend sda8 into the free space.

This is going to be dangerous and VERY slow, so instead what you should do is a full backup, repartition, and restore.

---

### Post by mc_tux on 2010-04-28
I see now, I messed my partition structure too much. I sure know it's very risky playing with partitions, had a bad experience and all-data loss too many times. This time, not having the ability to backup data, I'll reorganize my files instead of partitions, maybe reinstall whole thing, as 10.04 is released within a few hours :)

Anyway, booting from some live CD and moving partitions in the right order would solve the problem. Thank you for your answers.

[SIZE=2][SIZE=1]As an aside: I've used /dev/sda8 only for my music files, that they could be  reachable from any OS and kept nicely in separate partition. I do not  use separate partitions for file sharing between Ubuntu and Windows,  because Ubuntu can read NTFS, and there's a ext file system reader for  Windows[/SIZE].
[SIZE=1]P. S. 160 gb for hdd is so little these days.[/SIZE]
[/SIZE]

---

