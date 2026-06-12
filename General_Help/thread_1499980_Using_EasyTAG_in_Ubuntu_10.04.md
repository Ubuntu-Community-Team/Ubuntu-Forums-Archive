---
title: "Using EasyTAG in Ubuntu 10.04"
date: 2010-06-02
forum: General Help
---

### Post by ottabaub on 2010-06-02
I installed EasyTAG using the Ubuntu Software Center. It works but I'd like to have an audio player play the selected file. I tried the command "xmms -p" but xmms wasn't installed. I tried to install it only to find it was now xmms2 and nyxmms2 or something like that. That led me to Esperanza. Typically I can't find an good documentation on EasyTAG. (Is anyone surprised?) I just want to put a player in "Audio File Player" in the EasyTAG settings that will play the tune I've selected. Seems easy enough but if I put Rhythmbox, audacious2 or Esperanza, the app runs but the song doesn't play nor is it selected. I've spent about 3 hours of my day Googling for a solution. No way. Why is this so freakin' difficult?

---

### Post by cariboo on 2010-06-02
I would suggest using audaciuos, it is in the repositories, and is a replacement for xmms.

---

### Post by ottabaub on 2010-06-03
> **cariboo907 said:**
> I would suggest using audaciuos, it is in the repositories, and is a replacement for xmms.

Tried it and it runs but doesn't play the audio file I selected. I would have to search through my music, find it and select it. Useless!

---

### Post by lykeion on 2010-06-03
For me audacious works fine. It adds the selected audio file to the playlist and starts playing it.
I'm using Audacious v2.3 and EasyTAG v2.1.6

Maybe there is something wrong with the audio file you selected, have you tried with another?

---

### Post by oldos2er on 2010-06-03
> **ottabaub said:**
>  Typically I can't find an good documentation on EasyTAG. (Is anyone surprised?) I just want to put a player in "Audio File Player" in the EasyTAG settings that will play the tune I've selected. 

Have you seen [http://easytag.sourceforge.net/EasyTAG_Documentation.html](http://easytag.sourceforge.net/EasyTAG_Documentation.html) ? Scroll down to 2.Tips:

---

### Post by ottabaub on 2010-07-14
> **lykeion said:**
> For me audacious works fine. It adds the selected audio file to the playlist and starts playing it.
I'm using Audacious v2.3 and EasyTAG v2.1.6

Maybe there is something wrong with the audio file you selected, have you tried with another?

I forgot to subscribe to this thread so I didn't read your reply until today. Thanks for your comment.

I'm running Audacious 2.3 and EasyTAG 2.1.5. (I should upgrade.) I just tried it again and now it's working fine. What can I say? Interestingly though, when Audacious is run from EasyTAG it reverts to the default skin. And I can't change the skin back until I close it and run it from the Applications menu.

So my solution was to use the GTK version by running the command:
audacious2 -i gtkui

Cheers...

---

### Post by ottabaub on 2010-07-14
> **oldos2er said:**
> Have you seen [http://easytag.sourceforge.net/EasyTAG_Documentation.html](http://easytag.sourceforge.net/EasyTAG_Documentation.html) ? Scroll down to 2.Tips:

Hi. Thanks. I had read that and tried it but it didn't work. However, as you can read in my reply to **lykeion**, it's now working for me. Dunno why but why question it.

Cheers...

---

