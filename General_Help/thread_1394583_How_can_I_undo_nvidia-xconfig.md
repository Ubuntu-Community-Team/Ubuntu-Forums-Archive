---
title: "How can I undo nvidia-xconfig?"
date: 2010-01-30
forum: General Help
---

### Post by the_me on 2010-01-30
I think the title explains what I need to do. I ran nvidia-xconfig and now when I start up, all I get is gibberish on the screen.

I've looked around, tried "dpkg-reconfigure xserver-xorg" which did absolutely nothing, and was the only thing I could find that I figured was remotely related.

Any help or ideas would be greatly appreciated, I'd really rather not reinstall if I can avoid it.

---

### Post by pbrane on 2010-01-30
You can rename your existing /etc/X11/xorg.conf to /etc/X11/xorg.conf.bak and then restart the X server. You won't be using nvidia's proprietary drivers anymore. You will have to run nvidia-xconfig to set that back up. Running **sudo dpkg-reconfigure -phigh xserver-xorg** in a terminal should write a new xorg.conf though.

This link has some good info [http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400")

---

### Post by the_me on 2010-01-30
thanks for the advice, but a friend put me in contact with another and the solution was so easy I feel stupid.

I'm sure that method would have the same results, but all I did was unlink xorg.conf and restart, and it worked.

Thanks anyway though!

---

### Post by pbrane on 2010-01-31
Yes that works just the same as my suggestion. I was just trying to be cautious and rename the file instead og deleting.

---

