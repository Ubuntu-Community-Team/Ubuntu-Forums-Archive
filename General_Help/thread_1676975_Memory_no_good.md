---
title: "Memory no good?"
date: 2011-01-28
forum: General Help
---

### Post by piano_man9009 on 2011-01-28
I was working at my computer (ubuntu 10.10), installed some updates, tranferred a bunch of files from an external hard drive, then just kinda messing around.  skype logged out then crashed, pressed restart, which caused a blank window to come up.  anyways, i started it back up to be brought into busybox.  i restarted again, and ran the memtest, came back in 5 minutes and it had thrown about 13 errors.  I'm unfamiliar with memtest, is it specifically testing my RAM?  do those errors indicate that for sure i kneed new memory sticks?

---

### Post by darkhelmetchris on 2011-01-28
Generally speaking, yes.  When memtest reports errors, it's most likely that you have some bad ram.

However, in the past, I have also seen a plugged-up CPU heatsink lead to unpredictable errors when a CPU is running hot.  I would suggest that you check to see if your heatsink/fan assembly are plugged up with dust and leaving you with no airflow.

If your heatsink is not plugged, and your memtest still gives you errors, then checking the ram on another mainboard is a good test.  If you have more than one stick of ram, run memtest with just one stick installed, and repeat for each stick.  Perhaps you have only one bad stick of ram.

Good luck.

---

### Post by piano_man9009 on 2011-01-28
yeah, only one of my sticks was bad.  But now when i start up, it takes me to busybox, lists a few things and then won't let me type or do anything. (not that i'd know what i was doing anyways if i could type!) When i plugged in a thumb drive, it recognized it and listed that i plugged it in.  so i restarted and booted into ubuntu from my install thumbdrive.  when it starts up, i get an error report that palimpset has crashed.  when i try to mount my hard drives, it just sits there forever and never mounts. whats going on? i'd like to be able to at least access those hd's so i can back up my stuff onto an external.  (one hard drive is a back up of the other, but i can't access either right now, i literally got rid of my external backup yesterday.)

---

### Post by piano_man9009 on 2011-01-28
I can type in busybox now.
by the way, i took the bad stick out, just in case anyone thought i was stupid ;)

---

### Post by darkhelmetchris on 2011-01-31
Well, funny thing about faulty memory, is if you had it installed and your OS up and running, it's possible that you have written faulty data back to your partition.  So, the first thing to do is to try to repair the filesystem.  Boot into a LiveCD or LiveUSB and open up GParted.  You should be able to select your hard disk and see the partition(s) you want to repair.  If they have been mounted, unmount them - as running a repair on a mounted filesystem is a bad idea.  Once unmounted, right-click the partition and choose "Check" and see what happens.  Please post the output.

If all goes well, it should repair your partition and you should be able to access it again, just by opening it from your Nautilus, "Computer" listing, and clicking on your partition.

If that does not work, you might have to do a manual check from the command-line.  Be aware, that you will need to identify your partition clearly - you can find the partition listed in GParted.  If your partition is /dev/sdg1 you can check/repair it like this:
```
sudo fsck /dev/sdg1
```

Let's first see how that goes.

---

### Post by piano_man9009 on 2011-01-31
a graphical check says "the file system is NOT clean"
a manual check says:

fsck from util-linux-ng 2.17.2
e2fsck 1.41.12 (17-May-2010)
fsck.ext4: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

i had just started up the system and had not done anything to try and mount the hd.

---

### Post by darkhelmetchris on 2011-02-03
In order to run fsck, you'll need to unmount the partition.  Are you running your system directly or from a LiveCD/USB?  It's a good idea to do it with a LiveCD/USB.  If you are already doing that, then in your Nautilus file manager, you should be able to right-click and unmount.  Then you can run fsck.

---

### Post by piano_man9009 on 2011-02-03
Yes i'm on a live usb, i can't start up from my hard drives, thats the reason we're doing this remember?! haha.  and the hard drive isn't mounted when i tried to fsck.  i never did anything to mount it, there isn't an option to unmount it. only an option to mount it, which won't work, which again, is why we're doing this ;)

---

### Post by piano_man9009 on 2011-02-07
anybody wanna give me a hand?  i'd like to be able to run off something besides a live cd again.  and accessing my music would be nice :)

---

### Post by darkhelmetchris on 2011-02-09
> **piano_man9009 said:**
> Yes i'm on a live usb, i can't start up from my hard drives, thats the reason we're doing this remember?! haha.  and the hard drive isn't mounted when i tried to fsck.  i never did anything to mount it, there isn't an option to unmount it. only an option to mount it, which won't work, which again, is why we're doing this ;)

Oopsy, my bad there.  Okay, I have found some (rather surprising) information.  According to the following:
[https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/656526](https://bugs.launchpad.net/ubuntu/+source/e2fsprogs/+bug/656526)
It seems as if there may be a bug in the way that 10.10 handles checking ext4.

The current workaround seems to be to use a LiveCD/USB of 10.04 to run fsck against your partitions.  This seems to have worked for others.  I have been unaware of this type of bug as I elected to retain ext3 partitions in my 10.10 installs.  Hope this new information helps you.

---

### Post by piano_man9009 on 2011-02-11
all right, that got me a little closer! in the 10.04 live cd, i can fsck it, and even mount it, although i can't start up with the live cd if the hard drive is plugged in when i turn on the computer, it just sits there and shows a loading screen for ubuntu.  anyways, so i fscked it, and it says the file system is clean.  i mount it, and the easiest and quickest route for me is probably just to get my files off, and just do a clean install.  Problem is now, i don't have permission to read lots of what i want to take off of it.  So can i get permission while i'm on a live cd?

---

