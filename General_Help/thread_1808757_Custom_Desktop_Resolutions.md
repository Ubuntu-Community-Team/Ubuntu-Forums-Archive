---
title: "Custom Desktop Resolutions"
date: 2011-07-20
forum: General Help
---

### Post by TomAwezome on 2011-07-20
A few months ago I switched from Windows XP to Ubuntu 11.04. After switching, I had realized that for Windows, my resolution was 1280x768. For Ubuntu, the highest it could find was 1024x768.

After doing some searching, I had found a way to add my own in.

The following are the steps I used to get 1280x768:
```
cvt 1280 768
```
That gave me: "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync

I then did the following:
```
xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync
```

When typing xrandr, it showed me a new resolution was made: 1280x768_60.00

I then typed:
```
xrandr --addmode VGA1 1280x768_60.00
```

I went to System Setting > Monitors to find that 1280 x 768 (16:10) was added.

That was a while back. At that point, any time I tried to use that new resolution it would give me a large black bar on the right side of my screen taking up a good 1/6 of my screen. I was able to press things that were under that black bar, but couldn't see it.

I recently learned about a classic mode using GNOME instead of the new Unity. I tried the above commands in GNOME, and everything went well. There was no black bar, and, as said, everything looked good.

Then, filled with excitement, I switched over to Unity, and tried the above commands. They worked. There was no black bar, and the only side effects were that I had to reapply my desktop background.

Then I tried to switch to GNOME again.

I switched and noticed a quick popup, spitting out some strange code or something, with a monitor icon, and then it went away. My desktop was now in 1024x768. I did the above steps, and everything went fine.

This leaves me to believe that every time I reboot, log-out, or anything like that, I'll have to enter those commands back in.

I now have two questions:
One: How can I save that resolution so I don't need to keep putting the commands in every reboot?
and Two: Was I doing anything wrong with the commands, or was there anything I'm missing?

[[EDIT]]
> I switched and noticed a quick popup, spitting out some strange code or something, with a monitor icon, and then it went away.
I was able to snag a picture of this, it literately appeared for a good .5 seconds: [IMG]http://dl.dropbox.com/u/30616256/Screenshot-1.png[/IMG]

---

### Post by TomAwezome on 2011-07-21
Okay, I did more of a workaround then a complete solve, but whatever.

All I did was I bound "xrandr --newmode "1280x768_60.00"   79.50  1280 1344 1472 1664  768 771 781 798 -hsync +vsync" to shift+ctrl+alt+delete, and then I bound "xrandr --addmode 1280x768_60.00" to shift+ctrl+alt+insert. It didn't really solve the problem, but since it made it take around 4 seconds to do, I think I'll stick with it.

Thread Solved.

---

### Post by realzippy on 2011-07-21
..have a look here to make it permanent:

[http://ubuntuforums.org/showpost.php?p=10929081&postcount=8](http://ubuntuforums.org/showpost.php?p=10929081&postcount=8)

..also you could create a *xorg.conf* and add your modeline.

---

### Post by realzippy on 2011-08-22
Just cleaning up my subscribed threads.
Please set thread as solved (ThreadTools)...thanks

---

