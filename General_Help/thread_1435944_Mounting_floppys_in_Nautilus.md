---
title: "Mounting floppys in Nautilus?"
date: 2010-03-22
forum: General Help
---

### Post by auh2o on 2010-03-22
I have two floppy drives. As per fstab:

```
/dev/fd0 /media/floppy0 auto rw,user,noauto,exec,utf8 0 0
/dev/fd1 /media/floppy1 auto rw,user,noauto,exec,utf8 0 0
```If I want to access these in Nautilus, I have to pull up a terminal and enter

```
mount /dev/fd0(1)
```This because the only option Nautilus gives me on right-clicking a floppy entry is "Detect Media", which does nothing except briefly search the drive. (Might this have anything to do with all the floppys I have tried being FAT and not ext4, maybe?)

What I wonder is, is there no way I can mount the floppy drives from withing Nautilus, via a script or something? I am against using the terminal in all instances where it can be avoided. (Long-time Windows user...) ;-)

Also, in Puppy Linux, you get a fd0 icon on the desktop that stays put even when a floppy is not mounted. You can use that icon both to mount and unmount. Is there a way to create a launcher like that on the Gnome desktop?

I attached a screencap of what it looks like in Nautilus with both floppy drives mounted. Both "Floppy Drive" entries don't actually do anything at all -- they're completely useless. Could I maybe remove them altogether and make the floppy0 and floppy1 entries stay even when not mounted, so I can just right-click on them and mount?

And by the way - if you were going to reply "nobody uses floppys anymore", then don't.

---

### Post by auh2o on 2010-05-01
Just wanted to inform anybody whom it concerns that Nautilus mounting of floppys **works **flawlessly now after upgrading to 10.04. Must've been a Karmic bug.

---

