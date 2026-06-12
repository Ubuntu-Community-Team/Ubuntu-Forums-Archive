---
title: "Ubuntu launches in command line only"
date: 2011-05-02
forum: General Help
---

### Post by johnpr1 on 2011-05-02
I upgraded to Ubuntu 11.4. When it launches I log in in command line format and I stay there. Is there a command to get me into the GUI? Or do I need to re-install?

---

### Post by Rubi1200 on 2011-05-03
Hi and welcome to the forums :-)

We need some more information please.

1. what graphics card and how much RAM is installed

2. how did you upgrade; via the CD or Update Manager

3. what other operating systems are on the computer and do you have problems booting them

Finally, did you try either of these commands at the terminal:

```
sudo startx

sudo service gdm start
```

---

### Post by johnpr1 on 2011-05-04
Thanks for the reply. the commands you suggested do not work.
I have a Dell. P4, 3.4 GHz. 2 gig ram, Video card is Nvidia GeForce 7800 GT. I usually run  Windows XP as the main operating system. I upgraded by downloading Ubuntu-11.04.
I have reinstalled it. Now, when I try to boot into Ubuntu, the screen is mostly gibberish, white letters on black screen. Rebooting again allows me options, such as ubuntu, Linux 2.6.38-8-generic or ubuntu, Linux 2.6.38.8-generic (recovery mode). Neither of these work. Another of the several options is Ubuntu, kernel 2.6.20.16-generic which launches into Gnome desktop, but will not accept my username and password.
I figure I did something wrong. Can this be salvaged, or should I wipe out the partition and start new?

---

### Post by Hedgehog1 on 2011-05-05
We need to get a look at what shape your system is in after the install attempt.

Please boot off the LiveCD/LiveUSB, select 'TRY', and then:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Follow the instruction on the website and post the results here.

Please press the '#' button when posting and place the the script results between the two 'CODE' tags.

***The Hedge***

:KS

---

