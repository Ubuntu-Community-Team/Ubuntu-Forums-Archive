---
title: "Text consoles in karmic"
date: 2009-11-05
forum: General Help
---

### Post by breadlord on 2009-11-05
Hi,

I've just made a clean install of Karmic, and while there are a couple of teething problems, the main one is that when I switch to a text mode console (ctrl-alt-fx), instead of getting a login console, I just have a flashing carat in the top left of the screen. The console appears to be in vga (as opposed to olde fashioned text) mode, but tty8 is happily displaying messages from fsck - so I don't think it's a graphics issue.

I have to admit that while I'm far from a linux noob, this is almost certainly a piece of basic configuration that I'm unaware of.

Any help gratefully appreciated.

---

### Post by breadlord on 2009-11-05
Bump

---

### Post by dvlchd3 on 2009-11-05
I had this same issue with my laptop.  I found it was because of my proprietary driver installation for my graphics card.

Now that the driver is in the kernel, I have no issue.

Not sure if there is a fix since proprietary drivers are closed source...

---

### Post by Iowan on 2009-11-05
I had a [similar]("http://ubuntuforums.org/showthread.php?t=289272") problem - a few versions ago.

---

