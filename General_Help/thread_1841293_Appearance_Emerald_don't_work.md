---
title: "Appearance Emerald don't work"
date: 2011-09-09
forum: General Help
---

### Post by LLMB0611 on 2011-09-09
I was trying to remove unnecesary theme's that i never use. I always customize my own theme. and i deleted some things in Appearance-->Theme-->Customize, after i deleted one theme everything stoped working. I couldn't open Appearance, Update manager or some other things. I figured out what the problem was so i installed some small theme changer and changed the theme and got everything back working. That's not the problem. The problem is when i try to change a theme in Appearance nothing happens. some things change but not in a way they should. The same thing happens with Emerald. Emerald don't change nothing. In Apearance i can change icons, cursor, window border, controls, but the colors don't change?? Why is that? Should i maybe reinstall something?? (except ubuntu :D)


one more thing. in appearance-->theme-->colors if i click reset to defaults the whole ubuntu slows down, nothing responds and i have to restart

UBUNTU 10.10
AMD 3000+
2 GB RAM
NVIDIA G210

---

### Post by raja.genupula on 2011-09-09
follow this everything gonna be fine 

[http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/](http://ubuntugenius.wordpress.com/2011/05/22/ubuntu-11-04-fix-enable-emerald-themes-for-compiz-fusion-window-borders-title-bars/)

---

### Post by LLMB0611 on 2011-09-09
nope, didn't work for me. got an error when trying sudo make install
attached a file whit all the errors i got

---

### Post by snip3r8 on 2011-09-09
Add this ppa and upgrade emerald
[https://launchpad.net/~malteworld/+archive/compiz]("https://launchpad.net/%7Emalteworld/+archive/compiz")

---

### Post by Frogs Hair on 2011-09-09
I have tested the PPA and it works great with 11.04 . If Appearance Preferences are not working I'm not sure a Compiz PPA will help .

In 11.04 there is/was a bug connected to The package: ```
gnome-themes-ubuntu
``` 

This package caused a broken link in Appearance Preferences and the desktop in general I had to reinstall it. I discovered the problem when I used gksu nautilus an the error showed up in the terminal .

---

### Post by LLMB0611 on 2011-09-09
upgraded emerald, still didn't help. looks like i'll have to reinstall ubuntu. think i'll try 11.04 now.

---

### Post by snip3r8 on 2011-09-09
> **LLMB0611 said:**
> upgraded emerald, still didn't help. looks like i'll have to reinstall ubuntu. think i'll try 11.04 now.
Good luck,I didnt like unity at first but now I love it....

---

