---
title: "Can't Access Virtual Terminals"
date: 2010-05-12
forum: General Help
---

### Post by acidcj on 2010-05-12
Using 10.04 on my laptop, but I can't access the virtual terminals (ctrl+alt+f1-f6).  Instead I get a weird screen with apparently randomly generated lines, as they change each time I attempt to access them.  (Sometimes it is just a solid color.)  They also appear on shutdown/ switching user.  I'm using a VIA VX800 chipset.

Help? Fixes?

[IMG]http://i39.tinypic.com/14muh02.jpg[/IMG]

---

### Post by efflandt on 2010-05-12
Look through the release notes, especially [http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](http://www.ubuntu.com/getubuntu/releasenotes/1004#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)

---

### Post by acidcj on 2010-05-13
I should probably mention that I am trying to use a 1280x800 resolution After viewing your link, I tried setting the
GRUB_CMD_LINUX=
line to nomodeset.
(And then sudo update-grub)

This didn't work, and I found this website, (2 years old: [http://forums.fedoraforum.org/archive/index.php/t-170490.html](http://forums.fedoraforum.org/archive/index.php/t-170490.html)) it suggested setting the line to vga=872 or similar.  Further researching I found that this is now for the 1440x900 resolution.  Using these codes gave me 6 miniature terminals across the top of the screen, each visibly simultaneously responding to key strokes, but too small to be used.  The rest of the screen was filled with a pattern similar to above.  Similarly, while rebooting, what appeared to be the Ubuntu logo showed in each of the 6 mini-screens.

I then tried using hwinfo --framebuffer and found three 1280x800 resolutions at 0x03b6, 0x03b7, and 0x03b8.  I tried all three as they are, and as 0x3b6, etc.  None of these even give me a "mini-screen," just a different-but-similar pattern.

---

