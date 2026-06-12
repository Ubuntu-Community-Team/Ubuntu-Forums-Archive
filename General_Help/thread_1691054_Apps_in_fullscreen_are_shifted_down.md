---
title: "Apps in fullscreen are shifted down"
date: 2011-02-19
forum: General Help
---

### Post by eightballd on 2011-02-19
When I run apps like ZSNES or XBMC in fullscreen their output is clipped at the bottom.  It's like their output is shifted down about 20%.

Here are some screenshots of the two apps

[http://nevercertain.com/xbmc.jpg]("http://nevercertain.com/xbmc.jpg")
[http://nevercertain.com/zsnes.png]("http://nevercertain.com/zsnes.png")

I'm running Ubuntu 10.04 64bit with an Intel card.  I get the same behavior with desktop effects on and off.

uname -a 
Linux fry 2.6.35-25-generic #44-Ubuntu SMP Fri Jan 21 17:40:44 UTC 2011 x86_64 GNU/Linux

My xorg log: [http://pastebin.com/tWXQV27h](http://pastebin.com/tWXQV27h)

My video is output to my TV via a VGA cable.  

Unless one of these apps is running in full screen, everything is fine.  In fact, I can even run VLC or Movie Player in full screen with no problems.

Anyone have any ideas?

Thanks in advance,
James

---

### Post by eightballd on 2011-02-27
Bump

---

### Post by patrick_the_fat on 2011-02-27
If this is happening with only your game emulators, you might just need to go into the preferences and change the fullscreen resolution settings.  You can try 800x600 resolution, 24-bit, and maybe, just maybe, that will fix it!

Further, do you have Compiz enabled?  If so, try disabling/enabling some of the options (scale used to cause my windows to move back and forth every time I clicked).  Also, on most systems, you can hold alt and drag windows, making them pretty easy to move.  You might even be better off setting the windows to 'maximize', rather than going fullscreen.

---

### Post by eightballd on 2011-02-27
Hi, this happens with XBMC (which is not an emulator) and ZSNES.  It happens whether Compiz is turned on or off.

800x600 doesn't seem to help, unfortunately.

Thanks for the tip about maximize.  That's what I'm doing for ZSNES when I play.  Would love to figure out this problem and fix it because the situation really sucks for XBMC.  I normally use XBMC to watch videos on my TV, but now have to use VLC.

---

