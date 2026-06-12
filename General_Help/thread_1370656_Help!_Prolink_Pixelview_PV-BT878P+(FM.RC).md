---
title: "Help! Prolink Pixelview PV-BT878P+(FM.RC)"
date: 2010-01-02
forum: General Help
---

### Post by madjinji on 2010-01-02
I have a TV card
   
    [B]Pixelview PV-BT878P+(FM.RC)
    PHILIPS FM1216/PH hm
[/B]
First I've done many things to make the audio works and still nothing until I give up and after rebooting my machine I found out that it works but what exactly made it work I've no idea.
Unfortunately I had to change my system like formating everything and now i cannot make it work again, still good picture with no audio, I've tried every thing again you cold Imagen but still not working......

PLEASE HELP GUYS!

[B]P.S.
The is working with windows XP perfectly and i mad it work with ubuntu 9.10 once but i cannot do this again.[/B]

---

### Post by madjinji on 2010-01-04
Thanks people for passing by....:(
I've found a way to my problem, is to add these line  " **options bttv card=70 tuner=38 radio=1 gpiomask=0x3F audiomux=33,32,35,35,40 **" to " **/etc/modprobe.d/bttv** " and then reboot my machine and everything is done.

---

