---
title: "wmv streaming"
date: 2009-12-17
forum: General Help
---

### Post by mIXpRo on 2009-12-17
how can i play wmv files on the net ,means :
i have a site that i want to watch videos from it in format wmv live.

in windows (past ;)) when i click on the link it opens the windows media player and plays it .

but in ubuntu i tried with vlc totem but it didn't work , why ? how can i solve this problem ?

---

### Post by Physical Hook on 2009-12-17
Have you installed w32codecs and non-free-codecs ( Medibuntu ) ?

---

### Post by mIXpRo on 2009-12-17
i tired w32codecs , but non-free-codecs i didn't where can i find it ?

---

### Post by klemes on 2009-12-17
Try the mplayer-plugin.It supports wmv and also a handful of other codecs as well.
Install it by typing in the console:

```
sudo apt-get install mozilla-mplayer
```

---

### Post by mIXpRo on 2009-12-17
no, mplayer didn't work :(

---

### Post by amsterdamharu on 2009-12-17
Activate the nonfree packages. System -> administration -> software sources 
(in ubuntu 8 their called multiverse) check them
Firefox or mplayer will ask you to install the codec if you try and play wmv. If that fails you can try installing VLC player but then you have to copy the url all the time and paste them in vlc player.

If something fails please tell us what you've tried and what exectly fails (what message)

---

### Post by andrew.46 on 2009-12-17
Hi mIXpRo,

> **mIXpRo said:**
> no, mplayer didn't work :(

Can you post the address that MPlayer failed on?

Andrew

---

### Post by mIXpRo on 2009-12-17
when clicking on the link in firefox , window pop up asking me to choose between which programs i want to run it with , if i select mplayer it open , but it just gets stuck . 

[IMG]file:///home/mixpro/Desktop/Screenshot.jpg[/IMG]see attachment .

---

### Post by andrew.46 on 2009-12-17
Hi mIXpRo,

> **mIXpRo said:**
> when clicking on the link in firefox.....

If you can give the address of this page it will be a little easier to troubleshoot :).

All the best,

Andrew

---

### Post by mIXpRo on 2009-12-17
i'm a student in the computer science faculty at the israeli institute of technology (the technion)   
so this link to the technions server , the problem is that in order to watch these videos you have to be connected throw it's local area connection . 
it only gives permissions to a certain ips.

but anyway this is the link , try 
the address is : video.technion.ac.il

---

### Post by andrew.46 on 2009-12-17
Hi mIXpRo,

> **mIXpRo said:**
> the address is : video.technion.ac.il

Hmmmm.... can't play the stream directly and via Firefox there is an error box in ?Hebrew. Can you translate?

Andrew

---

### Post by amsterdamharu on 2009-12-17
When I try to open a random video from that site firefox asks me what application to open the link with, I choose vlc since mplayer never gets the codecs correctly installed automatically.
But VLC gives the following:
main error: Connection to video9.technion.ac.il port 1755 failed: Connection timed out

Link I tried to open:
mms://video9.technion.ac.il/Courses/Automata_Q/AUTOMATA%20AND%20FORMAL%20LANGUAGES-Q&A-01.wmv

Maybe mplayer doesn't handle connection timeouts very well you can try to open mplayer from console command open a stream and see what you get.

---

### Post by mIXpRo on 2009-12-19
> **andrew.46 said:**
> Hi mIXpRo,



Hmmmm.... can't play the stream directly and via Firefox there is an error box in ?Hebrew. Can you translate?

Andrew

it's just a warning for copy rights  and not to download this file on your system .
but after clicking ok it should play (at the technion network).

---

### Post by mIXpRo on 2009-12-22
nobody replayed that maybe means you don't know ,
well after a quit "research ;)" , a figured out the problem .
since this kind of video is for windows it is played as mms format .
in order to play it at linux you should change the format at your player to rtsp://"the file"
most recommended player is the vlc .

---

