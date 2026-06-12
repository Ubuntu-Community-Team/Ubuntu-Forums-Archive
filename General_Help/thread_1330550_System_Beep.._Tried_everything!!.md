---
title: "System Beep.. Tried everything!!"
date: 2009-11-18
forum: General Help
---

### Post by daviiiiiid on 2009-11-18
Hey guys.

I tried everything to get rid of the annoying system beep but it keeps on beeping!!

I dont know what to do anymore.. I put the sound theme to no sound in sound preferences.

The most promising was this one:
[http://friendlytechninja.vndv.com/2009/10/16/howto-fix-alert-system-beep-in-ubuntu-9-10-karmic-koala/](http://friendlytechninja.vndv.com/2009/10/16/howto-fix-alert-system-beep-in-ubuntu-9-10-karmic-koala/)

but I cant find "PC Beep". This is what I get:

&#9474;    < Master >     PCM        IEC958     IEC958 D    Ext Mic     Int Mic

---

### Post by estyles on 2009-11-18
I have a solution that involves a screwdriver and wirecutters... =)

Funny, I have the opposite "problem".  Since installing karmic, my system beep is gone.  Don't get me wrong, I'm not sad to lose it, but I just wonder why it quit working...

---

### Post by Gatorade on 2009-11-18
is it the beep when you shut down the computer?

if so, read this [http://ubuntuforums.org/showthread.php?t=1324120]("http://ubuntuforums.org/showthread.php?t=1324120")

should solve your problem

---

### Post by Giblet5 on 2009-11-18
> **estyles said:**
> **i have a solution that involves a screwdriver and wirecutters... =)**

funny, i have the opposite "problem".  Since installing karmic, my system beep is gone.  Don't get me wrong, i'm not sad to lose it, but i just wonder why it quit working...

+1

---

### Post by scouser73 on 2009-11-18
[[COLOR="Red"]**Disable The System Beep**[/COLOR]]("http://ubuntuguide.net/disable-the-annoying-beep-when-you-shutdown")

---

### Post by daviiiiiid on 2009-11-19
Thanks scouser. It now does it much less often. It still does from time to time.. I'll manage with this..

---

### Post by xtracool_protik on 2009-11-19
Hey daviiiiid
 If u have Gnome-alsa-mixer just open it and disable the beep, if not install it through synaptic and use it.
 However for some reason sometimes it doesn't save ur preferences over reboot I need to change my sound setting everytime after restart

---

### Post by jeb800e on 2009-11-19
System < Preferences < Sound

---

### Post by ivanvajar on 2009-11-19
Add this to the end of /etc/modprobe.d/blacklist:

> blacklist pcspkr

---

