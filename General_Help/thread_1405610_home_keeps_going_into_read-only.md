---
title: "/home keeps going into read-only"
date: 2010-02-12
forum: General Help
---

### Post by taddy_porter on 2010-02-12
I've got a Jaunty 32-bit system that's been running fine for some time. I came home today to find the /home drive mounted as read-only. This is a SATA drive formatted to ext4.

Ran fsck on it, tried a manual re-mount. All I can get is it to reboot fine, but within minutes it will suddenly show back up in read-only mode.

There's a message in dmesg about aborted journal, but I would have thought fsck would have fixed that.

Any way, I find the computer difficult to use without write capabilities, so any help would be appreciated.

---

### Post by rsay on 2010-02-17
I am dealing with a similar problem on my backup drive. I'm trying to figure out if it means I my  drive is going bad or if there is some kind of memory error issue. I am memtesting the computer while I'm at work today.

---

### Post by sefs on 2010-02-17
> **taddy_porter said:**
> I've got a Jaunty 32-bit system that's been running fine for some time. I came home today to find the /home drive mounted as read-only. This is a SATA drive formatted to ext4.

Ran fsck on it, tried a manual re-mount. All I can get is it to reboot fine, but within minutes it will suddenly show back up in read-only mode.

There's a message in dmesg about aborted journal, but I would have thought fsck would have fixed that.

Any way, I find the computer difficult to use without write capabilities, so any help would be appreciated.

Back up your data immediately. You may have physical disk damage that is progressive.  Do you have a utility like spinrite ([http://grc.com/spinrite](http://grc.com/spinrite)) to see if the disk is in danger of imminent failure or is over heating?

---

### Post by taddy_porter on 2010-02-17
Mine was a bad drive. I ran smartmontools and it identified the drive as failing. Moved everything to a new drive and haven't had any problems. It was actually a pretty painless process.

---

