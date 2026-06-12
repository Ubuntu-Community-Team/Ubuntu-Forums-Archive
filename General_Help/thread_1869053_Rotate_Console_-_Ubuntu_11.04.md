---
title: "Rotate Console - Ubuntu 11.04"
date: 2011-10-25
forum: General Help
---

### Post by hobleydd on 2011-10-25
Hello,  I am trying to get my server running with a rotated monitor (long story). I have fbcon loaded and nouveaufb running on the console:

# dmesg | grep nouveaufb 
[   16.056535] fbcon: nouveaufb (fb0) is primary device 
[   16.058073] fb0: nouveaufb frame buffer device

and I can see /sys/class/graphics/fbcon/rotate_all etc.  However, when I type:

echo 3 > /sys/class/graphics/fbcon/rotate_all

nothing happens. I have been searching for answers and the only thing I can find is that the kernel needs to have been compiled with support for console rotation.  Is that option compiled in for Ubuntu 11.04 (or 11.10 for that matter) ? Or should I be looking in a different direction?

Compiling a custom kernel looks tricky so I am hoping that I am missing something obvious.  Any help - greatly appreciated.

Cheers,
David

---

### Post by hobleydd on 2011-11-22
bump. anyone any ideas with this one?

---

