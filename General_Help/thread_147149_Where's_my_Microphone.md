---
title: "Where's my Microphone"
date: 2006-03-19
forum: General Help
---

### Post by Strumming Hippy on 2006-03-19
I'm running Breezy on a Dell Inspiron 4100 Laptop.  I'm having a lot of trouble with my sound.  I'll label these problems below.

Problem 1: Where's my Microphone
   My microphone captures no sound whatsoever.  Moreso, when I open the volume control, neither the microphone, nor the line-in have a record option.  What am I not doing?

Problem 2: Non Simultaneous Sound
   If I'm running xmms I can't run mplayer, and vice versa, this is so easy to avoid as to be trivial, but it kind of obnoxious to have to close the one program to use the other.

---

### Post by halfvolle melk on 2006-03-19
> Problem 1: Where's my Microphone
Open a terminal (Applications -> Accessories -> Terminal) and type
```
alsamixer
```
Use left and right arrows to navigate (to 'Mic' and maybe 'Mic boost), use 'm' to troggle a chanel on and of, use up and down arrow to increase or decrease the set volume and finally use escape to exit the set-up.

> Problem 2: Non Simultaneous Sound
I think JACK can do that, not sure though.
[http://jackit.sourceforge.net/](http://jackit.sourceforge.net/)

---

### Post by DOtSlaSHuCantCME on 2006-03-19
[QUOTE=Strumming Hippy]I'm running Breezy on a Dell Inspiron 4100 Laptop.  I'm having a lot of trouble with my sound.  I'll label these problems below.

Problem 1: Where's my Microphone
   My microphone captures no sound whatsoever.  Moreso, when I open the volume control, neither the microphone, nor the line-in have a record option.  What am I not doing?

Problem 2: Non Simultaneous Sound
   If I'm running xmms I can't run mplayer, and vice versa, this is so easy to avoid as to be trivial, but it kind of obnoxious to have to close the one program to use the other.[/QUOTE]

PROBLEM 1:Double click audio icon (on panel)Mic oiption should be under "CAPTURE", if its  not  present ,Press Edit and add mic (select).


PROBLEM 2: Im having the same issues. What i do is open totem second,totem seems to be the only app that works @ the same time (for me).

---

### Post by Strumming Hippy on 2006-03-20
Ok, tried adjusting the mic level through the terminal and also through the GUI.  although the levels are there and up and boosted,  I still get no incoming sound.  i.e. sound recorder can't hear, skype can't hear.  I can play sound just fine, but can't record anything.  

Further ideas?

---

### Post by halfvolle melk on 2006-03-20
Sure you got your mic plugged into the right connection point thingy?

---

### Post by Strumming Hippy on 2006-03-20
Interesting point.  Interesting both because I'm using an internal microphone, and more importantly because it caused the epiphone that solved the problem.  

To all of you with problems similar to the one I've mentioned here.  Either in the gui mixer, or even better in the alsa mixer mentioned above, make sure the mic is set to mic 1.  Turns out, somewhere along the line mine got switched over to two.  Darned if there ISN'T a second microphone.  Go figure.  

Thanks to everyone for their help on problem 1.  Still working at problem 2, and have discovered an all new annoyance with it.  No Skype while listening to xmms, means I might have to listen to the person on the phone.  Eee Gads, gotta change that.

Galen.

---

