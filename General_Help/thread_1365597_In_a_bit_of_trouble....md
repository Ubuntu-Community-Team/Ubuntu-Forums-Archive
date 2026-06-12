---
title: "In a bit of trouble..."
date: 2009-12-27
forum: General Help
---

### Post by plzdontkillme11 on 2009-12-27
Hi,

I was bored recently, so I decided to try out some of the other linux desktops available. I started with openbox; I installed it with 'sudo apt-get openbox.' I logged out, and selected the openbox session. It didnt't load so I force shut downed my computer.

Here's the problem: ubuntu isn't loading; the openbox is. All I see is a gray screen; no menu bars or anything. I need to know how to log back into my Ubuntu account. 


Help is much appreciated. Right now, i'm using my brother's windows laptop.  :[

Thanks.

---

### Post by jim_charlton on 2009-12-27
I assume you mean apt-get install openbox.?  My suggestion... When you boot the machine, hit ESC (for old GRUB) or SHIFT (for GRUB2) and choose the recovery mode from the list of options in grub.  When you get to a terminal window try 'sudo apt-get remove openbox´ and then 'sudo dpkg-reconfigure gdm' (assuming you were running gdm previously).  Or follow the more detailed suggestions on [http://ubuntuforums.org/showthread.php?t=355567](http://ubuntuforums.org/showthread.php?t=355567).

---

### Post by snowpine on 2009-12-27
You can select the desktop environment (Openbox vs. Gnome) from the GDM login screen (where you type your username and password).

"All I see is a gray screen" is an accurate description of what Openbox is supposed to look like. :)

---

### Post by plzdontkillme11 on 2009-12-27
Thanks guys for your responses!  I'll try your suggestion immediately.

---

### Post by plzdontkillme11 on 2009-12-27
Worked beautifully. Thanks!

---

