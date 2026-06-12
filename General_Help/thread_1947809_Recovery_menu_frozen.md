---
title: "Recovery menu frozen"
date: 2012-03-27
forum: General Help
---

### Post by tettnanger on 2012-03-27
I'm running Ubuntu 11.10 on an HP Compaq small form factor PC and everything has been great.  I recently screwed myself up by trying to add myself to a new group.  I did it wrong and wiped out all my other groups including the Admin group!  I figured I wasn't the first to do this and sure enough found all kinds of hits on how you can boot into Recover Mode as root and correct this.

Here's my problem though, I can boot into Recovery Mode, get the pink screen with the options but from there everything is frozen.  I can't pick the "root - Drop to root shell prompt" option and I've tried many times.

Has anyone else ever experienced this and know of any workarounds?  Is there any way to create some sort of bootable "recovery disk" maybe?

thanks!

---

### Post by tettnanger on 2012-03-27
Ok, solved my own problem.  Still not sure WHY this worked, but in case anyone else runs across a similar problem.  I had a number of USB devices plugged in (mouse, keyboard, old iPod, external HD, and a printer).  I unplugged ALL of those and plugged in an old PS2 keyboard.  Maybe it was just the keyboard, maybe it was all of the above, but it worked.  

I also had to remount the root file system as rw (got a lock on /etc/group until I did that) but was eventually able to add myself back to the admin group.

---

### Post by mörgæs on 2012-03-27
Thanks. Please mark the thread 'solved'.

---

