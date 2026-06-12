---
title: "Ubuntu wont let me copy shortcuts to my desktop."
date: 2011-07-28
forum: General Help
---

### Post by Del64 on 2011-07-28
When ever I try copying shortcuts to my desktop I get an error stating " Error While copying. There was an error getting information about '/' how the specified location is not supported". And when I try to copy thing is to my Cairo Dock bar it doesn't appear. I am running 11.04.
I have tried system repair and clean. so far nothing has happened.

How would I fix this issue?

---

### Post by jerrrys on 2011-07-28
all im seeing is a slash (/).  are you trying to make a home folder shortcut?  if so the command would be **nautilus**

---

### Post by fdrake on 2011-07-28
linux does not have shortcuts but link. I think your errors appears because you are trying to copy "/" folder on the desktop folder (inside "/"), which does not make sense.

to make links(symbolic)

```
ln -s / /.link
```
and you can move it arount where you want.

---

### Post by Del64 on 2011-07-29
I used to be able to hit the windows key in Nautilus and drag what ever program  link/shortcut I wanted on to the desktop. Now when I try that I receive  that error posted above.

---

### Post by aeiah on 2011-07-29
did you click the 'show more details' button, so you could, you know, see more details about the problem?

---

### Post by Del64 on 2011-07-29
> **aeiah said:**
> did you click the 'show more details' button, so you could, you know, see more details about the problem?

Yes. It says " The specified location is not supported"

---

### Post by jerrrys on 2011-07-29
you can remap that windows key

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remap+windows+key+ubuntu&sa=Search&cof=FORID:9#1031](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remap+windows+key+ubuntu&sa=Search&cof=FORID:9#1031)

---

### Post by Del64 on 2011-07-29
> **jerrrys said:**
> you can remap that windows key

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remap+windows+key+ubuntu&sa=Search&cof=FORID:9#1031](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=remap+windows+key+ubuntu&sa=Search&cof=FORID:9#1031)


I am uncertain how this will fix my issue? I have set meta to win keys and still the problem persists. This error pops up when ever I try to drag an icon onto the desktop from the apps list in Nautilus.

edit: Same issue as this user
[http://ubuntuforums.org/archive/index.php/t-1752273.html](http://ubuntuforums.org/archive/index.php/t-1752273.html)

---

