---
title: "Nothing Booting"
date: 2011-04-15
forum: General Help
---

### Post by k-mob on 2011-04-15
Hello all,

I've been happily running Ubuntu 10.04 on my laptop and desktop for many months now, but ran into my first truly frightening problem this morning.  I've been searching the boards all morning and am at my wits end trying to solve it.  I hope someone can help.

A little set up: I did a normal Install Updates this morning, but it seemed to hang.  Furthermore, after hanging, when I tried to save files it wouldn't let me, saying either the drive was unavailable for writing or write protected or something.

Well since I had a Restart Required message, I figured this would be a good time for a restart.  It ended up booting me right into  BusyBox v1.13.3 after telling me Target file system doesn't have /sbin/init/ and No init found. Try passing init= bootarg followed by a (initramfs) prompt.

I've gathered to mean that my hard drive isn't being mounted; most solutions to this begin with booting from a Live CD.  However, I made a Live CD with a USB stick, but when I try to boot from there, the splash screen pops up with the red/white dots moving around, but doesn't continue loading.  Pressing an arrow button lets me see the messages "can't open /dev/sr0: No medium found" and "unable to open /dev/sda".

If I try going into grub, I'll select one of over a dozen Ubuntu, with Linux 2.6.32-xx-generic options (with and without recovery mode), but again, those end up just kicking me to BusyBox again.

Any ideas?  I'm hoping/praying nothing's wrong with my hard drive, but I don't know how to proceed.

Thanks in advance!

---

### Post by K_45 on 2011-04-15
Is this a Wubi install, clean install, or dual-boot?

---

### Post by k-mob on 2011-04-15
Clean install.  Nothing else on there.

---

### Post by oldfred on 2011-04-15
You likely will need working USB or CD to make repairs. Does USB boot on your other computer?

You do get grub menu? And recovery mode does not work. Have you tried using e and edit line to remove quiet splash to see if it gives any more info on why it is not working?

---

### Post by K_45 on 2011-04-15
I'd burn Ubuntu to a livecd, then boot it up and run

```
sudo fdisk -l
``` - note down your root partition, probably sda1

followed by

```
sudo fsck -y /dev/[enter partition here]/
```

Answer yes. Reboot. Result?

---

### Post by k-mob on 2011-04-15
Okay, by using an actual CD instead of a USB drive, I got LiveCD to book up.  However, running fsck yielded "fsck.ext4: Device or resource busy while trying to open /dev/sda1; Filesystem mounted or opened exclusively by another program?"

Other posts have suggested running gparted or "e2fsck -f -y -v /dev/sda1".  But I'm not sure that any of that will work if it thinks the drive is already mounted....

Thanks for the help so far!

---

### Post by drs305 on 2011-04-15
Now that you have the LiveCD booted, please run the boot info script and post the contents of RESULTS.txt. It will give us a good picture of your boot situation.

[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by k-mob on 2011-04-15
Hm. For whatever reason (presumably the LiveCD boot has something to do with it), I have no internet.  Under wireless networks it says "device not ready".

---

### Post by k-mob on 2011-04-15
Okay, I found an Ethernet cable and got on a wired network for the time being.  I downloaded the script and ran it, but it seems hung up on "Seatching sda1 for information...."

Does this take a long time or did something go wrong?

Thanks.

---

### Post by K_45 on 2011-04-15
You may need to mount the partition yourself. Look here, third of the way down:

[https://answers.launchpad.net/ubuntu/+source/grub/+question/63005](https://answers.launchpad.net/ubuntu/+source/grub/+question/63005)

---

### Post by k-mob on 2011-04-15
When I type "sudo mount /dev/sda1 /media/root" (after creating /media/root), nothing happens.  It seems to hang; I don't even get a new prompt.  Not unlike when I tried bootinfoscript...

---

### Post by k-mob on 2011-04-15
Furthermore, I tried running Check on sda1 under gparted and got the following error:

** (gpartedbin:4772): CRITICAL **: murrine_style_draw_box: assertion `height >= -1' failed

and the "check and repair file system" operation remains in the bottom box as "1 operation pending"

CORRECTION: I applied the operation, but all it does is run e2fsck, which gave me the same error as before:
Filesystem mounted or opened exclusively by another program?

This is despite the fact that when I click on Information, it says the status is Not mounted

---

### Post by drs305 on 2011-04-15
You could also try Disk Utility via System, Administration.

Once you highlight the partition you may have the options to unmount and check the partition. If it won't unmount you may have to restart the LiveCD.

---

### Post by k-mob on 2011-04-15
Okay; when I tried to mount or check it under Disk Utility, it gave me some error about not having access (sorry I can't remember the details).  Under SMART Status it also said there were bad sectors.

So I rebooted (LiveCD), and reopened Disk Utility.  This time SMART Status reads "Not Supported", and when I clicked Mount Volume, the animated waiting icon just spins at the bottom of my big "77 GB ext4" box, but nothing happens.

Ideas?  Thanks again for the help!

(also, clicking on anything else (like Check Filesystem) now results in an error that the device is busy, "There is already a job running")

---

### Post by k-mob on 2011-04-15
I rebooted again and was able to "successfully" run Check Filesystem, but it just reported "File system is NOT clean"...

---

### Post by drs305 on 2011-04-15
Can you now run:
```

sudo umount /dev/sda1
sudo e2fsck -f -y -v /dev/sda1
```

I don't know if the Disk Utility actually tries to fix the partition, but probably not if it only reports it is not clean and doesn't offer to repair it.

You haven't mentioned Windows so I suppose you aren't looking to at least be able to boot that OS ...

---

### Post by k-mob on 2011-04-15
Uh, I'm almost willing to try anything at this point.  I'm downloading SLAX, as I've read another thread where someone had similar troubles but SLAX LiveCD was able to run e2fsck and fixed his problems.

In the meantime, I still get:
e2fsck: Device or resource busy while trying to open /dev/sda1
Filesystem mounted or opened exclusively by another program?

---

### Post by k-mob on 2011-04-15
Booting up with SLAX and then running e2fsck did the trick!  I can see my hard drive! Go figure...

Thanks for everyone's help!

Only one weird thing: all of my windows' frames look goofy.  Definitely different than normal.  Not sure that SLAX can permanently change any of those settings...

Also, should I be worried about an Update error I got that I can only do a partial upgrade due to probably whatever caused my trouble in the first place?  I don't know how big a deal it is....

---

### Post by drs305 on 2011-04-15
Assuming you have recovered a working system, I would advise not running the partial upgrade at this time, since you don't know what broke the system.

I'd make a backup of the entire partition using some sort of backup utility (rsync, partimage, fsarchiver, or even dd) before I tried doing any updates.

After a few days, to ensure the repositories contain all the upgraded packages, you could try to do another update. If you get an error message at that point, you could post it and we could help you further.

---

### Post by k-mob on 2011-04-16
Fantastic, thanks.  Backing up right now.

---

