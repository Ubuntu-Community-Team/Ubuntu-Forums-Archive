---
title: "Anybody in the US have the Univision world cup stream working?"
date: 2010-06-26
forum: General Help
---

### Post by sloggerkhan on 2010-06-26
I've been watching the world cup via ESPN360, which works fine on linux with flash.

But because for some idiot reason today's game (US v Ghana) is broadcast only, it appears that I'll have to watch it on Univision...

Not a big deal except that NO videos seem to work on their website under Linux... Can anyone confirm or do you know a workaround?

!!!!! I really want to watch the game... !!! 
([http://futbol.univision.com/](http://futbol.univision.com/), click to watch live.)


!!! Edit: Update: Works on my netbook, just not my desktop!!????!!!

---

### Post by TroN-0074 on 2010-06-26
I have ubuntu 10.04 Lucid with flash and the video in univision is working fine

---

### Post by sloggerkhan on 2010-06-26
Yeah, I don't have any idea why it might work on my netbook but not my desktop... maybe the 64 bit flash wrapper?

Anycase, since I can watch on my netbook, it's not a big issue.

---

### Post by WinterRain on 2010-06-26
> **sloggerkhan said:**
> maybe the 64 bit flash wrapper?



Yeah probably. If you want real 64bit flash without the wrapper:

Remove any flash you have installed, and get the 64bit flash file here [http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz](http://download.macromedia.com/pub/labs/flashplayer10/libflashplayer-10.0.45.2.linux-x86_64.so.tar.gz)

Then extract it and put it in /usr/lib64/mozilla/plugins and restart firefox. Works perfect for me.

If you are unsure how to do this, to extract the file, just right click and "extract here". Make sure it's on your desktop. Then do in terminal: (you can copy and paste it)
```
sudo cp ~/Desktop/libflashplayer.so /usr/lib64/mozilla/plugins
```
Restart firefox, done.

---

