---
title: "My last 3 problems... I hope"
date: 2010-08-23
forum: General Help
---

### Post by colmeweb on 2010-08-23
Hi, 
I am somewhat new to Ubuntu and have been wanting to get off of Vista. I have been able to solve all of my problems so far, but these 3 are giving me a real time. I am running 10.04 on a Toshiba Satellite A215.


[LIST=1]
[*]My biggest problem is that after I suspend my computer my wifi stops working. I have tried finding answers in the forums but so far none of them have worked. I don't know my hardware specs so if you want to know you are going to have to tell me how to find it, sorry.
[*]I can't seem to get Ubuntu to connect to my television. When I plug the VGA in Ubuntu detects the tv but there is nothing on the screen and the tv screen says that there is an invalid source.
[*]Lastly i setup a keyboard shortcut to put my monitor to sleep with the code below. But the problem is that the screen only goes off for a second and then comes back on.
xset dpms force  off/suspend/standby
[/LIST]
If anybody out there can help me with any of these issues I would be very great-full.

---

### Post by rollin on 2010-08-23
Hi.  For #3 you could try the script here: [http://alexcabal.com/turn-your-laptop-screen-off-with-a-keyboard-shortcut-in-ubuntu-karmic/](http://alexcabal.com/turn-your-laptop-screen-off-with-a-keyboard-shortcut-in-ubuntu-karmic/)

---

### Post by silbak04 on 2010-08-23
Problem number 1: When suspending your computer...you are trying to save more power...and therefore your wifi will be disabled if you suspend your computer...and to find your hardware specs you can just run this in a terminal ```
lshw
```

Problem number 2: This is probably more of a graphics care problem...you're probably going to need to look up the driver support for this.

Problem number 3: Just run this in a terminal to put computer to sleep```
$ sudo /etc/acpi/sleepbtn.sh
```Hope that helps!

---

### Post by colmeweb on 2010-08-24
Thanks for the link, the script just caused my screen to flicker off and on. One step closer to what I want though. :)

---

### Post by rollin on 2010-08-24
> **colmeweb said:**
> Thanks for the link, the script just caused my screen to flicker off and on. One step closer to what I want though. :)

Your welcome! Sorry to hear it didn't work out which is even more frustrating considering it's mean to solve that precise issue :-k
I'm out of ideas unfortunately, hopefully if you hang on you may find someone else with the same system who can help a bit more. While your waiting this (oldish) article has some info from users of the same laptop which could help your investigations: [http://www.linlap.com/wiki/toshiba+satellite+a215](http://www.linlap.com/wiki/toshiba+satellite+a215). 
I hope you manage to get some answers and things fixed and up and running soon. Otherwise perhaps just start a new thread with your Laptop name in it as well and hopefully it will attract a similar user. I hope it works out and good luck! :smile:

---

