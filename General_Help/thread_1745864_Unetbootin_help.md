---
title: "Unetbootin help?"
date: 2011-05-01
forum: General Help
---

### Post by [Shawn] on 2011-05-01
Okay, I've been trying to find ways to install "Puppy linux" on my dell dimension 2600 with 256MB ram, Seeing as my cd-rom drive doesn't work, I found out about unetbootin and thought i'd give it a shot, So, I downloaded it, selected "Puppy linux" and selected it to boot from USB drive, I figured it would work until I got an error saying that it doesn't work so and so. I selected hard drive and it went on ahead, but I figured if I did that i'd just be slowing my pc down even more then what it is if it doesn't install correctly! Does anyone have a clue what can be done? Any help will be appreciated!!
:)

---

### Post by jprobe on 2011-05-01
> **'[Shawn] said:**
> Okay, I've been trying to find ways to install "Puppy linux" on my dell dimension 2600 with 256MB ram, Seeing as my cd-rom drive doesn't work, I found out about unetbootin and thought i'd give it a shot, So, I downloaded it, selected "Puppy linux" and selected it to boot from USB drive, I figured it would work until I got an error saying that it doesn't work so and so. I selected hard drive and it went on ahead, but I figured if I did that i'd just be slowing my pc down even more then what it is if it doesn't install correctly! Does anyone have a clue what can be done? Any help will be appreciated!!
:)

I use MultiSystem ([http://liveusb.info/dotclear](http://liveusb.info/dotclear)) that I found out about on pendrive to do my USB installs.  But I used the Puppy USB creator that comes stock w/ Puppy to make my Puppy USB.  If your machine's BIOS won't run a USB right off, you can install WakePup onto a 3.5" floppy as a go between.  Wakepup is a .pet package that you can download from the Puppy repos.

---

### Post by Artemis3 on 2011-05-01
Unetbootin doesn't work with all machines, for example many Intel boards from Pentium D era refuse to boot from an usb made by unetbootin; but would work with one made by ubuntu's Startup Disk creator, or DDing a downloaded image. So yes, try Puppy's own USB creator first.

Also consider Lubuntu, or use the ubuntu minimal iso and install just what you really need...

---

