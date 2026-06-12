---
title: "Video mode not supported after kernel update"
date: 2011-10-01
forum: General Help
---

### Post by MSich on 2011-10-01
Using 10.4.  Yesterday I updated my linux kernel through the updater, to 2.6.32-34.  Prior to this I have had zero problems for over a year.  After the required restart I get the message "video mode not supported".  This has never happened before.  I swapped out my MAG monitor and hooked it up to my LCD tv, no change.

I booted I booted with the LiveCD, mounted my filesystem and checked the /etc/default/Grub file.  The line GRUB_CMDLINE_LINUX was set to nothing, GRUB_CMDLINE_LINUX="" to be exact.  I edited it to reflect 318, which is 1024x768, 24 bits, if I'm not mistaken.  Saved GRUB and did a grub update, rebooted and still nothing.

That is probably the extent of my knowledge about that, but I don't know why I would have this issue.  The system boots all the way up, I can see it on the network and access shared files.

I didn't find much on here, but I have noticed some issues with Nvidia cards, which I also have.

Ideas are appreciated.  I really don't want to re-install over something that seems so simple.

---

### Post by dcstar on 2011-10-02
> **MSich said:**
> Using 10.4.  Yesterday I updated my linux kernel through the updater, to 2.6.32-34.
........
I didn't find much on here, but I have noticed some issues with Nvidia cards, which I also have.


Unless the Nvidia drivers for that kernel **and** your system have been released then you may get issues like this.

I am wondering how 2.6.32-34 has been released for 9.10 systems, this kernel is only now available to 10.04 in the "Proposed" repository.

---

### Post by MSich on 2011-10-02
I am using 10.04 LTS.  I guess I haven't updated my info in a while.

---

### Post by dino99 on 2011-10-02
better to use:

GRUB_CMDLINE_LINUX="vga=791 splash quiet"

then: sudo update-grub

---

### Post by MSich on 2011-10-14
I've had very little time to work on this.  However, none of these suggestions has worked, which really surprised me.  The problem is worse than I thought.  I was able to boot up and do a Ctrl Alt F1 and get to a prompt.  Now it's all squished at the top of the screen.  Even if I boot into a recovery menu it is squished at the top, which it wasn't before.I'm probably going to re-install. I can boot with the LiveCD just fine and don't have any video issues.  I will mount my file system and save my Home folder.Some items show as locked.  I should be able to change the owner I those, I think so I can save them.

---

