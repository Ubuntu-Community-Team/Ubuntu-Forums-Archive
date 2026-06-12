---
title: "Genius easy pen i405"
date: 2010-01-02
forum: General Help
---

### Post by Dracona on 2010-01-02
hello, my son recieved an Genius easypen i405 for x-mas, and i have not been able to find any drivers to get it running in linux. ubuntu does nothing when i plug it into the usb port.
im running ubuntu 9.10 64 bit. i have tried installing the drivers under wine, but wine dont like it. anyone have any ideas?

Dracona

---

### Post by Dracona on 2010-01-02
this is probably a stupid question, but would wacom drivers work for the easy pen i405 ?

---

### Post by Favux on 2010-01-03
Hi Dracona,

To figure out what driver and .fdi (device information file) you need we need to know the manufacturer of the tablet that has been branded by Genius as the easy pen i405.  In a terminal enter:
```
grep -i name /proc/bus/input/devices
```
and let's look at the output.

---

### Post by Dracona on 2010-01-03
dracona@dracona-linux:~$ grep -i name /proc/bus/input/devices
N: Name="Power Button"
N: Name="Power Button"
N: Name="Macintosh mouse button emulation"
N: Name="Logitech USB Gaming Mouse"
N: Name="UC-LOGIC Tablet WP5540U"
N: Name="G15 Gaming Keyboard"
N: Name="G15 Gaming Keyboard"
N: Name="HDA Digital PCBeep"

---

### Post by Dracona on 2010-01-03
> **Favux said:**
> Hi Dracona,

To figure out what driver and .fdi (device information file) you need we need to know the manufacturer of the tablet that has been branded by Genius as the easy pen i405.  In a terminal enter:
```
grep -i name /proc/bus/input/devices
```
and let's look at the output.
Favux, after reading your reply and following your suggestion, i did a search on the name reported by the command you gave.

i then found this How To from [B][U][COLOR=black]drpjkurian
[/COLOR][/U][/B][http://ubuntuforums.org/showthread.php?t=1337260](http://ubuntuforums.org/showthread.php?t=1337260)
and was able to get the tablet working!!!!!!!!!!!
after completing the how to i noticed that **_[COLOR=black]drpjkurian[/COLOR]_** gave you Favux credit for it.

"I acknowledge the help of [COLOR=Blue]**Favux**[/COLOR] and give credit to him who helped me a lot to install the wizardpen driver."
I also would like to thank you very much for your help Favux. 
I would also like to thank DRPJKURIAN for the How To.

the both of you have stopped me from having to install windows on my 100% Ubuntu system.

---

### Post by Favux on 2010-01-03
Hi Dracona,

Outstanding!  Nice work.  You're welcome.

---

### Post by wormite on 2010-02-19
Thank you Favux and Dracona, I am going to buy the product now wish me luck.

---

### Post by Scroobytec on 2010-04-21
Hi Favux

Thanks to you and drpjkurian I installed my new Genius Easy Pen i405 in next to no time on Ubuntu 9.10 (64 bit). All working fine, now we just have to see how well it will work in 8 day time when I upgrade..

---

### Post by Maharbal on 2011-02-17
I have just tried my Genius Easy Pen i405 on OpenSuse 11.3/64 (my first Os. But I also use Ubuntu.). This goes out of the box with the proper drive which ii can be found in this repo:

[http://download.opensuse.org/repositories/home:/alexqwesa/openSUSE_11.3/](http://download.opensuse.org/repositories/home:/alexqwesa/openSUSE_11.3/)

The characteristics of the hardware are (lsusb):
[I]
Bus 002 Device 004: ID 5543:0004 UC-Logic Technology Corp. Genius MousePen 5x4 Tablet[/I]

I think there could be a pressure problem (I think this is always at max), but i'm going to investigate next days.
Thank you very much for this thread which made me understand everything I needed to setup this tablet!
:D

---

### Post by Maharbal on 2011-02-17
In my last post I said there was a pressure problem. I was wrong. It was a issue of Gimp setting. Thanks again.
:-)

---

### Post by Favux on 2011-02-17
Hi Maharbal,

Welcome to Ubuntu forums!

Glad we could help you getting your easy pen working.  Nice job.

---

### Post by jpxsat on 2011-03-12
@Maharbal could you tell please how did you manage to configure The Gimp??

It's the last thing for me to do!!

---

### Post by Favux on 2011-03-12
Hi jpxsat,

You have to configure the extended input devices, i.e. stylus.  See the screenshots near the bottom of the [Wacom wiki]("https://help.ubuntu.com/community/Wacom").

---

