---
title: "After download, how to reclaim the CD player"
date: 2010-09-21
forum: General Help
---

### Post by mmcl on 2010-09-21
I'm continuing to slog through getting back to a "normal" relationship with my computer after my 10.1.04 re-install.  Right now, the CD player is not accessible. Instead of whatever the list said before, now it says, "U3 System." When I click on that, it says:
autorun               launchpad              Launch U3

Will someone please  advise me on how to get back to being able to play CDs on my computer?  

Also, while I'm at it:  There's a DVD slot, but I can't get it to open, although a light goes on when I push the button; any advice on how to use it? (I've never used it in the 6 years I've owned this machine.)

Thank you,

Martha

---

### Post by oldos2er on 2010-09-21
What type of CD are you trying to access when you see the 'autorun' error?

The DVD drive not opening sounds like a hardware error.

---

### Post by mmcl on 2010-09-21
Actually, I'm trying to access the CD player capability.  The last CD I had put into the slot was the Ubuntu download.  When done, I removed it and inserted a music CD (I still listen to CD's...) 

Before 10.4, when I inserted a music CD, an icon would appear on the desktop; I would seek out rhythm box music player and click on the CD to play it.

Now, a different icon, labeled "U3 system," appears.  I've gone to "Places" and looked for the CD player (forget what it used to be called -- media or something).  It's not there; instead is this "U3 system".  That's what I clicked on and got the three icons/messages: autorun, launchpad, LaunchU3.

---

### Post by oldos2er on 2010-09-22
Can you run ```
cat /etc/fstab
``` in a terminal, and post the output here?

---

### Post by mmcl on 2010-09-22
Is this what you're talking about? (below)

Martha



martha@martha-desktop:~$  cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=846792d3-d24e-43a0-9a84-e94f6163ad6b /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda7 during installation
UUID=c3f711b3-a1b2-4f48-b5c4-9d6e721e2f4a none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0

---

### Post by oldos2er on 2010-09-24
Does your machine have a floppy drive? I was wondering based on the info I found here: [https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/437415](https://bugs.launchpad.net/ubuntu/+source/devicekit-disks/+bug/437415)

---

