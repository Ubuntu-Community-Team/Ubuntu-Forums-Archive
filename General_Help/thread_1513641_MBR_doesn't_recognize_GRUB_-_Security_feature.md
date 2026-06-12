---
title: "MBR doesn't recognize GRUB - Security feature?"
date: 2010-06-19
forum: General Help
---

### Post by AlphaLexman on 2010-06-19
Some months ago an update crashed my GRUB. I did some fixes via CLI, but MBR does not boot to GRUB. I HAVE to put in a bootable/live CD with 'boot to first hard disk' option to get to GRUB. Without the boot disk, boot loader just freezes at CD-ROM(s).

At first, I felt this was an annoyance, after a few weeks/months? I felt like it was a security feature. Anyone who turns on my computer will not get ANY grub or windows login and think that the box is junk. You HAVE to put in a live CD and 'boot to first hdd' to get to grub before you have access to the machine (when it is off). 

Now, if someone turns on my machine, and they (amateur) would think my machine isn't even bootable (or maybe think THEY did something).

I have begun to actually ENJOY this added security measure and just wandered what boot or init files might be the cause/effect of this situation.

I know the computer isn't working as it should, but I kinda like it...

---

### Post by Mark Phelps on 2010-06-20
While I understand that this inconvenience may make you feel that your machine is more secure .. but consider that, if anyone can really "get to your machine", it should then be a simple matter to either (1) insert their own boot CD, or (2) remove the hard drive and make off with all your data.

Once folks have physical access to a device, aside from full disk encryption, there's really nothing you can do to make your data secure.  And, given the right hardware, all full disk encryption does is delay their access, not prevent it.

---

