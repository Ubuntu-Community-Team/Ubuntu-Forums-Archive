---
title: "Need help getting BEL to sound using vim"
date: 2011-03-09
forum: General Help
---

### Post by kline on 2011-03-09
Guys,

I have a bum shoulder in general and do not watch the screen while I type; instead, I watch my fingers.  A few months ago I upgraded to 10.10; I'll upgrade to 11.04 shortly.  For unknown reasons , when I upgraded to 10.10, the beep that I had figured out how to more/less make work, stopped working.    Because I've always been a lousy typist and do not hit keys with enough force, I can't always tell when I've hit ESC using vim.  So lots of times I wind up typing many words in ALL CAPS when I've hit the caps-lock key.  

I'm running Debian and Ubuntu on this desktop and two laptops and wants to make the ESP key have nice clear BEEP after I hit the escape key.

tia, people.

---

### Post by Habitual on 2011-03-09
What terminal do you use please?
```

sudo grep pcspkr /etc/modprobe.d/blacklist.conf
```

Is it blacklisted?

This link talks all about this subject. Sorry if I am all over the map.
My pc speaker doesn't work either atm on my laptop. So I am right there with you.

[http://superuser.com/questions/22767/enable-system-beep-in-ubuntu](http://superuser.com/questions/22767/enable-system-beep-in-ubuntu)

HTH.

Edit:

I tried everything I could find on the subject.
modprobe, added pcspker to modules file, alsamixer, gnome-alsamixer, installed beep. NOTHING WORKED.
No beep for me either in terminal period, let alone vi(m)

Sorry, I suck sometimes.

---

### Post by kline on 2011-03-10
> **Habitual said:**
> What terminal do you use please?
```

sudo grep pcspkr /etc/modprobe.d/blacklist.conf
```

Is it blacklisted?

This link talks all about this subject. Sorry if I am all over the map.
My pc speaker doesn't work either atm on my laptop. So I am right there with you.

[http://superuser.com/questions/22767/enable-system-beep-in-ubuntu](http://superuser.com/questions/22767/enable-system-beep-in-ubuntu)

HTH.

Edit:

I tried everything I could find on the subject.
modprobe, added pcspker to modules file, alsamixer, gnome-alsamixer, installed beep. NOTHING WORKED.
No beep for me either in terminal period, let alone vi(m)

Sorry, I suck sometimes.


My display is a widescreen that I bought two years ago; the desktop is a barebones box that a friend help me upgrade.  The computer is a 4-CPU Amd with builtin sound that plays web radio and other audio.  Some months ago I _did_ manage it to make a loud noise whenever I had ESC.  I think I had to select some beep.wav file and it turned out to be pretty bad.  Since I use both Gnome and KDE, it could have been either ....

I'll keep poking around.  I miss those beep!!

---

