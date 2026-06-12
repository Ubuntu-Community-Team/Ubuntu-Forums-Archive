---
title: "running on usb key - always get unclean shutdown"
date: 2009-07-03
forum: General Help
---

### Post by allerretour on 2009-07-03
I'm running Ubuntu on a usb key.  I originally wanted to use the usb-key Live CD idea with persistence, but I could never get it to work right.  Then someone suggested just installing normal Ubuntu (jaunty) on the key with grub on the key and booting off of that.  That works great.  I installed with ext 2 because I had heard (maybe wrongly) that this limits the writes to the key, which I'd heard could wear out.  At any rate, works great.  I really see no difference compared to running off the hard disk, except that it's a bit slower, which doesn't matter for the applications I'm running.

As I said, works great EXCEPT for one thing.  I always get an unclean shutdown message when I reboot. In checking for errors on /dev/sdc2, it always finds errors, and then asks me to do a manual fsck.  This usually returns a message about an unattached inode (don't know what that is) and asks me if I want to attach it to /lost+found.  Sometimes I get a message about a bad ref count also.

Anyway, I just answer yes yes yes and it boots up fine after that.  But I systematically get this unclean shutdown message, even if I just boot up, and then shutdown right away.  Anyone have an idea why this might be?  I'm definitely not pulling the key before the system is totally off.  Could it be related to the ext 2 file system?

Like I said, other than this problem, I love this running-off-the-usb-key solution because it allows me to borrow my friend's computer without touching his system (or him touching my files).  Thanks.

---

### Post by aesis05401 on 2009-07-03
[http://bbs.archlinux.org/viewtopic.php?id=68664]("http://bbs.archlinux.org/viewtopic.php?id=68664")

I haven't tried this yet, but I am also running on USB (utility keys that I would like to be able to hand out to people), and will need to find a solution.  

Please post back if you try this and it works.

---

