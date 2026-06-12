---
title: "TV Tuner software"
date: 2011-03-19
forum: General Help
---

### Post by Jancsy on 2011-03-19
Hey there! I've got a Gigabyte TV Tuner card which provides software/player for windows only. Does anyone know how to make it work on ubuntu too, please? It's Gigabyte GT-P6000. Thanks in advice!

---

### Post by marin123 on 2011-03-19
does it connect to usb?
it can work in vlc, but you have to enter frequencies manually if its dvb-t.
i can write you step by step instructions if you need them.

---

### Post by Jancsy on 2011-03-19
Hey marin123! No, it's not USB. It's a PCI. Any ideas how to install a driver or something which will make it work?

Thank you in advice!

Cheers!

---

### Post by Handssolow on 2011-03-19
Perhaps Kaffeine might be your answer.

It worked for my USB digital TV tuner. The only hitch I had here was a faulty aerial connection, there was a short. Once I'd re-soldered the plug it worked fine.

---

### Post by Jancsy on 2011-03-19
The problem is that i don't really know if it's dvb-t or what, i'm too noob for this, actually new to ubuntu :P I'll try that. Thanks! Other opinions are welcome too :)

---

### Post by Jancsy on 2011-03-19
I've installed Kaffeine, I don't see it anywhere. Can't start it :/

---

### Post by laceration on 2011-03-19
You have to set up firmware or drivers(different things to do for different devices) to make it work before you get to the software. [http://linuxtv.org/wiki/index.php/Main_Page](http://linuxtv.org/wiki/index.php/Main_Page) is a comprehensive source for info, I did a quick google for that card.  I think its an analogue card.  This is weird for a lot of the world which has switched over to digital tv.  If you can't find your card at linuxtv you might do a 
```
$ lspci
```
at the command line to find the chip that is on the card and go from there.  Post the result of the above command here if you need help identifying the chip.

---

### Post by fragos on 2011-03-20
Run "lsmod |grep tv" and you'll see what TV driver your system loaded. For example if you see bttv then you can install the tvtime application which will automatically configure for your card. If you see ivtv as your driver you'll need to install mythtv. Bttv is the only one I have any experience with.

---

