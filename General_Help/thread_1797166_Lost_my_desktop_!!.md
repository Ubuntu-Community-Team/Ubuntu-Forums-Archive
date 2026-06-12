---
title: "Lost my desktop !!"
date: 2011-07-04
forum: General Help
---

### Post by eipapp on 2011-07-04
Don't know what happened but had to re-boot my computer and when it came back up I lost my desktop. The only thing showing is the wallpaper. I have NO Launch bar, NO Ubuntu button, NO MeMenu, No Global Menus - NOTHING. What can I do to restore my desktop ?
If I click anywhere on or around the edges of the desktop I get 0.
If I right click, of course, it will let me change the desktop appearance from the standpoint of wallpaper, fonts, themes, etc.

Thanks,
Bruce

---

### Post by holycow131415 on 2011-07-05
Probably the easiest thing you could do and not waste hours of time is to download and burn ubuntu on a cd or usb, boot to the livecd so that you can backup your files, and then reinstall ubuntu.

---

### Post by wildmanne39 on 2011-07-05
> **eipapp said:**
> Don't know what happened but had to re-boot my computer and when it came back up I lost my desktop. The only thing showing is the wallpaper. I have NO Launch bar, NO Ubuntu button, NO MeMenu, No Global Menus - NOTHING. What can I do to restore my desktop ?
If I click anywhere on or around the edges of the desktop I get 0.
If I right click, of course, it will let me change the desktop appearance from the standpoint of wallpaper, fonts, themes, etc.

Thanks,
BruceHi, did you change setting in compiz, if so you can look in my signature below this text and click on reset unity and compiz and just reset compiz, then if you want to change settings in compiz like for the cube or desktop effects go to this link and you should have no problem.
[http://amazingubuntucube.blogspot.com/](http://amazingubuntucube.blogspot.com/)
if you did not change setting post back what you did before this happened.

---

### Post by mikejonesey on 2011-07-05
or do "Alt+F2" "metacity --replace" to sort things out temporarily?...

---

### Post by hawthornso23 on 2011-07-05
Looks to me like your unity desktop is broken. I assume you are running natty? Changed a few compiz settings? Unity can sometimes break like this, usually as a result of changing  compiz settings.

BTW if you are running natty then  metacity --replace  is bad advice. On top of the original problem you'll now have the extra problem of having killed compiz which unity depends on. 

To fix the broken unity desktop   ctrl alt F1  to bring up a terminal login. Then run

```
unity -- repair
```
or
```
unity --reset
```
Both work (actually I think these are equivalent.)

If you ran  metacity --replace then run 

```
compiz --replace &
```

to get compiz going again. Then reboot.

Good Luck

---

### Post by eipapp on 2011-07-05
That did it !!!!!!!!!! (hawthornso23) You're a genius.

Did: unity -- repair
re-booted then did: unity -- reset and presto it came back as before.
Can't begin to thank you enough.
Yes, I'm ashamed to admit that I was indeed messing around with compiz settings but I assure you that won't happen again. I've learned my lesson.
Thanks again man........... you rock.

Bruce  (Pennsylvania, USA)

---

