---
title: "Speed Problems!"
date: 2006-03-21
forum: General Help
---

### Post by jbritz22 on 2006-03-21
I have noticed some slight speed problems when running ubuntu 5.10.

It runs videos good, but the mouse drags, and the animations to close windows are really slow, etc. Mp3s are also very staticky for some reason, they are staticky for a bit, then go into normal playback. Any suggestions?

Anyway to disable visual enhancements such as window animations?

---

### Post by taurus on 2006-03-21
What is the spec of your machine and do you use any composite with X?

---

### Post by jbritz22 on 2006-03-21
Hmm... 

Intel Pentium III 600 MHz
256mb SDRam
Tnt2 16mb Video Card

Its ran windows 98 through windows xp mce, and mandrake linux. Could it be gnome that is slowing it down, I dont remember these slowdowns with mandrake /kde.

---

### Post by IYY on 2006-03-21
I think it's Gnome. Here are somethings you can do:

Change from metacity to xfwm4. Here's are [instructions]("http://ubuntuforums.org/showthread.php?t=88393") for this.

Disable animated minimizing, opaque moving and resizing. This is done in **gconf-editor**, under **apps > metacity > general > reduced resources**.

Just don't use Gnome and switch to XFCE, IceWM or Fluxbox. On one of my older machines I have a nice setup of IceWM, using Nautilus to render the desktop.

User a lighter theme. The Human theme is quite heavy on resources. Themes like Mist are much better for slower systems.

---

### Post by jbritz22 on 2006-03-21
Thank you a lot!!! I will test these when  I get home, I might try xfce!

---

### Post by virgule on 2006-03-21
A **scheduler** change will help a lot.. This is a somewhat-advanced tune but it does bring noticeable results. 
I have been suggested two ways. I used both.. One is to add a simple script in /etc/rcS.d/. The other is to add a kernel argument in GRUB.

You can see on what your current scheduler is set on with:
```

cat /sys/block/*/queue/scheduler
```

Script:
You need to open a **terminal** window then run gedit via sudo because you'll  need administrator priviledges.

```

sudo gedit

```

Paste all this in the window and save the file as **S08ioscheduler** in **/etc/rcS.d/**
Quit gedit.
Of course, you can subdue 'cfq' for whatever your scheduler of choice is. There is four: **noop, anticipatory, deadline** or **cfq**. **anticipatory** is the slow default.. mine is on **cfq**
```

#!/bin/sh
for f in /sys/block/*/queue/scheduler; do
echo cfq > $f
done

```

Last step is to set the eXecutable flag on the file.
```

sudo chmod +x /etc/rcS.d/S08ioscheduler

```

Kernel Argument in GRUB:
Put "elevator=????"  in GRUB, where ???? is either **noop, anticipatory, deadline** or **cfq**. Reboot and enjoy your new speed.

---

### Post by jbritz22 on 2006-03-22
I installed fluxbox and changed the scheduler settings and its running faster, I also switch from firefox to epiphany and noticed a speed increase. Still notice a bit of slowdown when multitasking, but it IS a P3 so I guess I can't expect much. Thanks for all the help.

---

