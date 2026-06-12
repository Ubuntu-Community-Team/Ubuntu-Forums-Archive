---
title: "Realtek ALC861"
date: 2009-11-27
forum: General Help
---

### Post by modustollens on 2009-11-27
I have been trying to get my sound going on 9.10.

I followed the advice of many threads but no avail.

My card in my laptop (a toshiba a110) is a Realtek ALC861.


'lspci'  shows that ubuntu thinks my audio device is a ati card (but that is my video card).

The sounds prefs. box does not list any hardware devices to consider.

Back to XP for me 'til I come up with a solution to make this ubuntu box make noise.

Any suggestions?

---

### Post by cascade9 on 2009-11-27
I havent tried my Realtek (889) under ubuntu, so I'm not 100% if this is the best, or only way, but I'm pretty sure you need to dl the drivers from Realtek. 

[http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false](http://www.realtek.com.tw/downloads/downloadsCheck.aspx?Langid=1&PNid=14&PFid=24&Level=4&Conn=3&DownTypeID=3&GetDown=false)

Agree to that junk (tick next to "I accept to the above"), next, go to "Unix (Linux)" down the bottom, dl the driver, unzip it, follow the instructions in the 'read me' file. Hopefully that works.

---

### Post by gladbeast on 2009-11-27
did you try this one?

[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by modustollens on 2009-11-28
I tried the advice in that thread.  But 9.10 was really unstable and constantly crashing my machine.  It was impossible to do much of anything for more than about 10 minutes.  Hence I installed 9.04 instead.

Now I can hear sound. But the volume is way too low.

I opened alsa mixer.  But I cannot make the master go to any value but 0.
I followed the tread about chnging the value. But no luck, again.


Any suggestions?

---

