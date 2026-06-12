---
title: "Recovering removed desktop background image"
date: 2010-03-26
forum: General Help
---

### Post by pipalpani on 2010-03-26
Hi

I'm an absolute newcomer to ubuntu and require help with something please!
Have accidently removed a desktop background image (lotus/pond) and would very much like to have it back. Would someone please tell me how to do this? I've read in Help that this image is not removed from my computer but don't know how to proceed. Many thanks.

---

### Post by gordintoronto on 2010-03-26
If you right-click on an empty part of the desktop, one of the options is "Change Desktop Background." In the Background tab it will show you the known backgrounds, so you can select what you like.  You can also Add any image on your system.

---

### Post by gmargo on 2010-03-26
Exactly which image did you delete?  Was it /usr/share/backgrounds/FlordeLoto.jpg?  That is from the **ubuntu-wallpapers** package, and you can reinstall it from the command line with: 
```

sudo aptitude -V -R reinstall ubuntu-wallpapers

```(Ignore this if gordintoronto is right and you only need to change the wallpaper selection.)

---

### Post by pipalpani on 2010-03-26
> **gordintoronto said:**
> If you right-click on an empty part of the desktop, one of the options is "Change Desktop Background." In the Background tab it will show you the known backgrounds, so you can select what you like.  You can also Add any image on your system.
Thanks very much gordintoronto...and thanks also to gmargo!

---

