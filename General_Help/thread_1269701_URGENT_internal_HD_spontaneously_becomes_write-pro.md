---
title: "URGENT: internal HD spontaneously becomes write-protected"
date: 2009-09-18
forum: General Help
---

### Post by fictivetoast on 2009-09-18
I'm really perplexed on this one and am desperate for help - will be moving to Europe in 3 days, so need to get this resolved asap.  Sincerely hope it isn't a hardware failure.

I have a new Acer 3810t laptop with a 500GB internal HD, purchased about 2 weeks ago.  Initially it came preloaded with Vista X64, and I made room for the karmic alpha.  Things ran beautifully for 2 weeks.  In the recent updates on Karmic, something really strange happened to my partitions, and I was getting ionode orphan corruption errors.

So I tried reformatting and installing Jaunty.

Within about 2hrs of use on the reformatted partitions, my root HD suddenly becomes read only, with the error "block device /dev/sda1 is write-protected" getting spit at me.  Upon reboot, FSCK runs and finds all sorts of new orphan errors.

I've tried writing a clean MBR from a ubuntu live cd (using both GParted and fdisk), creating new partitions, and reinstalling.  After an hour or two of use the same problem pops up.

I've tried fresh installs using both EXT3 and EXT4, and in both cases eventually get this problem.

What the heck could be going on?  Is my hard drive completely borked?  Is there something else I should do to try to scrub the MBR?  :confused:

Please please please help me if you guys have any ideas, I'm incredibly stressed and am afraid that it might be a hardware issue requiring service (which will be impossible for me to arrange for at least a month as I'm moving to Europe, rendering me without a computer in a foreign country for that time).

EDIT: A bit more info -- every time the issue has arisen while running apt-get in a terminal installing/updating packages, which suddenly spits out errors along the lines of, "failed to delete [package name]: Read-only file system".  I've often been copying files over to the internal HD from an external NTFS backup drive simultaneously, in case that could somehow be related.


Running sudo mount -o remount,rw / yields:
```
mount: block device /dev/sda1 is write-protected, mounting read-only
```

---

### Post by dandnsmith on 2009-09-18
I'd be very wary of assuming a hardware fault on the basis of something happening with (only) an alpha-release OS.
Have you tried Vista again, or did you wipe it?
What about putting a stable release on (dual booted if necessary)?

Some parts of Europe are really quite civilised, really!!

---

### Post by doas777 on 2009-09-18
you mentioned that fsck turned up errors right?
does your /etc/fstab contain a parameter like this one for your root drive
```
errors=remount-ro
```?

if so, then that is likely why your drive is mounted read only. I would reboot into recovery mode and run fsck on the drive again, adn reboot

---

### Post by fictivetoast on 2009-09-18
I've fully reformatted the HD and have put 9.04 on there, and the error has cropped back up, which is why I'm worrying that it might be hardware.

Could something about the MBR have gotten borked up that would result in continued hard drive errors despite a reformat?

Am running 9.04 right now, and most recently rebooted following the "write only" error, and was walked through fixing a bunch more orphaned nodes and all sorts of junk in FSCK.  Finally rebooted smooothly, but I'm waiting to see if the HD jumps back into read only again in a few minutes as it's had a history of doing.  :(

As for Vista, I tried installing through restore CDs via an external DVD-drive, and the Acer software was unable to even find the hard drive... which means MBR almost certainly got borked, right?  After creating a new partition table with Gparted on the Ubuntu live cd, I was able to get the Acer CDs to restore vista, but never bothered to boot into it and marched forward into reinstalling Ubuntu until this error cropped up again.

As for Europe, I'd say most of it's considerably more civilised than the states :)  It's just that I'm moving alone, don't yet have an apt, will have a lot of work to do upon arrival, and am anxious about having to figure out international warranty service with Acer if need be.

---

### Post by falconindy on 2009-09-18
I had a drive explode on me 2 days ago and this is the behavior it was exhibiting. I suggest making an exact image of the disk (using dd) as soon as possible if you want to preserve anything on it.

---

### Post by fictivetoast on 2009-09-18
> **doas777 said:**
> you mentioned that fsck turned up errors right?
does your /etc/fstab contain a parameter like this one for your root drive
```
errors=remount-ro
```?

if so, then that is likely why your drive is mounted read only. I would reboot into recovery mode and run fsck on the drive again, adn reboot

Indeed it does.  Just rebooted into recovery and ran fsck as suggested.  All sorts of errors were found.  fsck seems to have fixed them without too much trouble.

The question is though, why would these errors be cropping up?  Is it normal on a fresh install to have tons of corruption issues on the hard drive like this?

---

### Post by doas777 on 2009-09-18
> **fictivetoast said:**
> Indeed it does.  Just rebooted into recovery and ran fsck as suggested.  All sorts of errors were found.  fsck seems to have fixed them without too much trouble.

The question is though, why would these errors be cropping up?  Is it normal on a fresh install to have tons of corruption issues on the hard drive like this?
do you shut down gracefully?

---

### Post by fictivetoast on 2009-09-18
> **doas777 said:**
> do you shut down gracefully?

The laptop usually ends up winding down then sits with a blinking cursor instead of actually powering off.  So no, not entirely, though according to most of the messages it gives me in the terminal it seems like most services have been stoped.  I then have been using [ALT + SysRq + [R E I S U B]]("http://kember.net/articles/231/reisub-the-gentle-linux-restart") to reboot it as softly as I can.

---

### Post by dandnsmith on 2009-09-19
I think I'd be trying 2 things at this stage - of course I've no idea what your time pressure is as a result of the impending move.

1. get a new HDD, image the old, and thus insure against failure of it

2. try an earlier release, such as 8.10. I've seen problems with certain hardware as a result of some of the kernel (and other) feature changes - sometimes the changes help, and sometimes not.

Good luck

---

### Post by fictivetoast on 2009-10-05
Update incase anybody else experiences this issue : while older releases didn't resolve anything, the new Karmic beta seems to be controlling the HD correctly.  Phew.

---

