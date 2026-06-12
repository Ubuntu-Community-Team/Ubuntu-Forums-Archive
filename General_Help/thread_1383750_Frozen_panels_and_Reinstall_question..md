---
title: "Frozen panels and Reinstall question."
date: 2010-01-17
forum: General Help
---

### Post by crosspicker on 2010-01-17
I had a bit of a situation yesterday that I have since been able to fix by reinstalling Ubuntu-Studio but it did raise some questions that I would like to hear what people have to say.

First what happened was I a Panel that would auto hide, I created another panel and not thinking moved it over the panel that was hidden. That caused all my panels to freeze and be unaccessible, I couldn't right click and nothing was visible including the "Start" button. The gnome applet was running because when I did a restart a pop-up notified that gnome panel was running and asked if I wanted to restart anyway. After a restart I tried to wait out whatever gnome panel was trying to do but it would hang and stay like that even after a restart. Another thing I noticed leading up to all of this is that every once in a while when I would open an application the three circles in the top right corner of the window wouldn't be there so I would have to right click on the window and close it.

I did a reinstall and everything is fine, which brings me to my questions!

  1. Without access to the start button couldn't get into terminal to try *killall gnome panel* or something like that, I assumed that there had to be keyboard short cuts to open a terminal window because F1 would open the help window, which I did do some searching in but don't have the time or patience for. Is there default keyboard short cuts and do I have to mess with config files to set them?

  2. Also on the reinstall I only reinstalled the / partition and setup everything exactly the way I had it before, but what I want to know is, is there anyway when reinstalling to get Ubuntu to use the existing Home partition that I already had instead of creating a new home folder and treating the old Home folder as a mounted drive?

I'm trying to get as much info as I can so any 2 cents you can add is appreciated.

---

### Post by tom4everitt on 2010-01-17
1. ctrl+alt+fX (X between 1 and 6) will take you to shell. 

2. choose advanced when installing ubuntu. Then you can choose which partition you want to use as your home partition. Same home folder basically means same settings however, so you might have end up with the same problem again.

---

### Post by pastalavista on 2010-01-17
Try doing a full reinstall, from the live CD, in MANUAL mode. At the partition menu, UNCHECK the 'format' boxes for all the partitions. On the one you need to designate as /home, do it here. Just enter '/home' as the mountpoint for that partition. Remember DO NOT FORMAT the drive. Then click 'install.

---

### Post by tom4everitt on 2010-01-17
Oh, you can still make your home partition mount as your home by editing /etc/fstab. 

There's tons of guides how to do this, get back to me if you can't find any suitable/need help.

---

### Post by crosspicker on 2010-01-17
> **pastalavista said:**
> Try doing a full reinstall, from the live CD, in MANUAL mode. At the partition menu, UNCHECK the 'format' boxes for all the partitions. On the one you need to designate as /home, do it here. Just enter '/home' as the mountpoint for that partition. Remember DO NOT FORMAT the drive. Then click 'install.
Just to clarify, when I reinstalled and formated my root partition I needed to remount the Home partition. Now that I think about it, it makes sense and is one of those things that is so simple that not seeing that in the first place is just so maddening.

---

### Post by crosspicker on 2010-01-25
I'm posting how I fixed this for whoever might read this in the future.

In a earlier post by Tom4Everitt he suggested that mounting my Home partition would cause the same problems that I was having before my reinstall, that is exactly correct so I had to set my panel back to it's default settings to fix the problem. I found 2 sites to help me with my problems, the first being Gnome Panel crashing I found the fix here [http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/]("http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/")

Then I found this tutorial for mounting my old /Home partition here  
[http://help.ubuntu.com/community/Fstab]("http://help.ubuntu.com/community/Fstab")

Now all is good and I appreciate the help.

---

