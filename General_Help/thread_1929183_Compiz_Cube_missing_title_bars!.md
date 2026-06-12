---
title: "Compiz Cube missing title bars!"
date: 2012-02-21
forum: General Help
---

### Post by bugz000 on 2012-02-21
Hello, i am running ubuntu 11.10 on my laptop and i keep hitting this issue where the title bars are missing at seemingly random times - they just DISSAPEAR!

no borders, no title bar, minimise maximize and close buttons are gone and i have issues bringing windows to focus - i have Compiz installed and i use it ALOT.

i have tried many solutions on the internet - none work!
but i have had a breakthrough - i have found out how to replicate this - i open three windows on different virtual screens - i maximise one window then flip between the screens a bit - after about 5 seconds of this - the window title bar is missing on all non-maximised windows! WAA!

**compiz --replace** works  but it moves all of my windows to one screen and it takes a while to complete - it is not ideal - is there any working, permanent solutions for this? :(
thankyou for your time,
Bugz000

---

### Post by bugz000 on 2012-02-21
bumpitty bump!

D:

---

### Post by PhantomTurtle on 2012-02-21
I found [[COLOR="RoyalBlue"]this[/COLOR]]("http://ubuntugenius.wordpress.com/2011/05/21/ubuntu-11-04-fix-restore-missing-title-bars-window-borders-in-compiz-fusion/") when i was looking around. It is for Ubuntu 11.04. I have never had a problem like that but it's worth trying though. All it says is to open CCSM, scroll down to effects and enable Window decoration.

---

### Post by bugz000 on 2012-02-21
AHA yes - that DOES work too - SOMETIMES - but mine is not disabled - it is enabled, so i disable it and nothing happens, i enable it and it lags for a long time- then the windows appear again - although the last time i did this it completely went screwy and resulted in no title bars and the window decoration not having any effect,

i am aware of most the workarounds and i appreciate your help - but i (and many others) are looking for a more permanent solution to this,

Thankyou for your time,
Bugz000

---

### Post by bugz000 on 2012-02-22
ACHOO!
sneez'd to the top D:

---

### Post by bugz000 on 2012-02-22
welp, bump :(

---

### Post by bugz000 on 2012-02-23
bump :(

---

### Post by PhantomTurtle on 2012-02-23
I remember on Ubuntu 9.10 I used to have the same problem. This was because of some of the desktop effects I enabled on compiz(I think it was of the desktop cube effect, I really can't remember). I could never really get it fixed though Try playing around with the settings a little bit. Good luck with that and sorry I couldn't come up with a better solution.

---

### Post by stinkeye on 2012-02-24
Instead of using
```
compiz --replace
```


Just reload window decorations with
```
gtk-window-decorator --replace
```

Add a keyboard shortcut if you need to use it a lot.


When running in the terminal, so the decoration remains once the terminal is closed use...
```
gtk-window-decorator --replace **& disown**
```

---

### Post by bugz000 on 2012-02-24
WOW! that works brilliant- mapped it to Ctrl W - instant fix-  they just pop right back up without any lag!

thankyou!! :)

---

