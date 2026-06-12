---
title: "edit the boot list file"
date: 2010-02-27
forum: General Help
---

### Post by motorhead_1 on 2010-02-27
I want to modify the GRUB boot list as I have many extra entries for ubuntu (about 8 entries), two memory tests and two for win xp. 

I've followed [these]("http://ubuntuforums.org/archive/index.php/t-393809.html") instructions as I had the same problem (couldn't see my linux drive)

> So, to change grub you need to first mount the partition. So create a directory on your desktop: from the terminal type 'cd ~/Desktop' - then 'mkdir here'. This should create a directory called 'here' on the desktop.

Then mount the Linux partition to it:

sudo mount /dev/hda1[or whatever it is] ~/Desktop/here

... then open up grub for editing

sudo nano ~/Desktop/here/boot/grub/menu.lst

And make the changes to the 'default' line so it points to Vista
the thing is that I can't see anything in my terminal after this...

[[IMG]http://img299.imageshack.us/img299/6870/screenshotkz.th.png[/IMG]]("http://img299.imageshack.us/i/screenshotkz.png/")

---

### Post by altjx on 2010-02-27
sorry im a little lazy, click my username & find all posts by me
<-----
i have a post about the same thing, it got resolved

EDIT: [http://ubuntuforums.org/showthread.php?t=1398700](http://ubuntuforums.org/showthread.php?t=1398700)

---

### Post by motorhead_1 on 2010-02-27
Thanks!!!

---

### Post by altjx on 2010-02-27
> **motorhead_1 said:**
> Thanks!!!

yw

---

