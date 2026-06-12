---
title: "Jaunty locks up completely under mild stress"
date: 2009-07-29
forum: General Help
---

### Post by V for Vincent on 2009-07-29
Hey there,

I've been having this issue for a week or so. Whenever I fire up a reasonable number of applications, ubuntu locks up on me. Say, if I'm running firefox with about three tabs open and then launch thunderbird and rhythmbox, my system is guaranteed to lock up and require a hard reset (or ctrl-alt-f2 + console reboot). Mouse kind of moves but won't click, keyboard doesn't respond so gnome-doing my way out of this situation is not an option, either. The system doesn't slow down before this happens - if it does, that kind of heralds an inevitable lockup.

It doesn't seem to be caused by any particular application. I get it when I'm using epiphany or opera, as well, or, sometimes, when I'm just running t-bird or rhythmbox rather than both. My system's a dell latitude D600, ext3. Probably not enough info, I know, but just fire away some terminal commands and I'll provide output.

---

### Post by Sef on 2009-07-29
1) How much ram do you have?

2) Have you checked it to see if it is still good?

---

### Post by MichealH on 2009-07-29
Have you got EXT 4 file system or EXT 3 because EXT 4 has bugs as its said in [this post]("http://ubuntuforums.org/showthread.php?t=1133719").

---

### Post by MockY on 2009-07-29
Boot your computer from a live CD and select the option to test your memory in order to exclude that as a cause.

---

### Post by marasmus on 2009-08-11
I have the exact(!) same problem on a Thinkpad X60s with 2GB of RAM, running a standard installation of Jaunty (plus Intel gma gfx drivers). I did a full 24 hour Eurosoft PC-Check on it with no errors found, so it's definitely a software issue. I suspect it came after the most recent software update. System monitor in Gnome does not report any processes running wild. The way I experience it is Ubuntu gradually getting slower and slower and slower, until all I can do is move a stuttering mouse cursor around.

---

