---
title: "Uninstalling 10.4 in dual boot"
date: 2012-05-02
forum: General Help
---

### Post by rs321 on 2012-05-02
Ubuntu 10.4
HP Pavilion g7
Dual partition Win 7

Folks,

This brand-new laptop is a piece of crap and I recommend it to nobody but I own it and I'm stuck with it so I'm trying to make the best of a poor situation.  The laptop is falling apart and HP support insists the problems lie with Ubuntu being on the machine, but the problems are within the machine because they are common to both Win7 and Ubuntu.  Specifically there's no sound and when I'm writing something the characters will suddenly start appearing elsewhere in the document, but I have my doubts those problems would occur across the partitions if it weren't the machine's fault.

To the point, HP support will not help so long as Ubuntu is installed, but I found two obstacles to losing it.  One is that when Ubuntu is installed it replaces the "Rescue Sector" (I think that's what it's called) in Win7 with grub which renders my rescue disks useless, and the other is that HP doesn't include an installation disk with it's computers but rather gives the owner a one-time opportunity to create his own rescue disks instead.  I made the disks but, as I mentioned, they are useless.

It will take me a long time to speak anything nice about HP again but in the meantime does anybody know how to circumvent the problem of uninstalling my beloved Ubuntu while leaving Win7 intact?

Thanks for any ideas,

-Randy

---

### Post by billyseth on 2012-05-02
You could look into the Gparted live CD, and delete your ubuntu partition, then resize your windows partition back to the full drive.
But keep in mind this might(probably) will cause problems with grub that will need fixing also.

---

### Post by HereInOz on 2012-05-02
How about buying a new HDD (or borrow a suitably nuked one from a friend) and install that in the computer, setting your original one to one side.  Once you have the new hard disk in place, use the recovery DVDs to reinstall the system back to factory.  

If that doesn't work, call up HP, tell them you had a hard disk failure, you have installed a new hard disk, and the recovery DVDs don't work.

By the way, the problem of the letters appearing elsewhere in the document while typing is often caused by your left thumb hitting the touchpad while you are typing, which repositions the cursor where the mouse pointer currently sits.  May not be a problem with the laptop at all in relation to this issue.

---

### Post by rs321 on 2012-05-03
Folks,

Thanks for your responses and suggestions.  I spent a pleasant (?) few hours on the phone to India and finally found someone who was short tempered but knew how to reinstall the drivers with Ubuntu on the computer, then I inactivated the touch pad and everything seems back to normal.

Thanks again.

-Randy

---

