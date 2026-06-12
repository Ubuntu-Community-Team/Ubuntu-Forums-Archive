---
title: "nautilus crashing"
date: 2009-08-03
forum: General Help
---

### Post by Darebnicek on 2009-08-03
For no obvious reason nautilus has started to crash. Even icons on desktop disappeared. in console I get message segmentation fault and in dmesg something like:  segfault at 0 ip 00000000 sp b585796c error 4 in nautilus[8048000+191000]. Any idea what is the reaseon

---

### Post by Primefalcon on 2009-08-03
> **Darebnicek said:**
> For no obvious reason nautilus has started to crash. Even icons on desktop disappeared. in console I get message segmentation fault and in dmesg something like:  segfault at 0 ip 00000000 sp b585796c error 4 in nautilus[8048000+191000]. Any idea what is the reaseon
I've had this happen myself here and there myself, though rarely, press alt+f2 and type nautilus to get it all back anyhow usually form an unstable app though

---

### Post by Revolutionary101 on 2009-08-03
You could also do a reboot.

---

### Post by Primefalcon on 2009-08-03
> **Revolutionary101 said:**
> You could also do a reboot.
why reboot when you don't have to? just an alt+f2 and then typing nautilus in the box and hitting enter will get everything back

---

### Post by Darebnicek on 2009-08-03
nope. nope
It it crashes every time. It started today about 12 hours ago. No updates or installation at that time. I tried to delete .nautilus, but did not help.

---

### Post by Revolutionary101 on 2009-08-03
> **Primefalcon said:**
> why reboot when you don't have to? just an alt+f2 and then typing nautilus in the box and hitting enter will get everything back

Well I have done that before and it will open the nautilus file manager back but it will not get the icons back on the desktop. Only a reboot will get the icons back on the desktop.

---

### Post by Primefalcon on 2009-08-03
> **Revolutionary101 said:**
> Well I have done that before and it will open the nautilus file manager back but it will not get the icons back on the desktop. Only a reboot will get the icons back on the desktop.
It's always got the icons back for me but anyhow it sounds like a deeper issue here, what are you running when this happens? is there any app that you have plugged into nautilus such as dropbox or ubuntuone or nautilus-right-click or such?

---

### Post by Primefalcon on 2009-08-03
also try this from your home
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

---

### Post by Darebnicek on 2009-08-03
nothing serious is running, just firefox. And it happens even after reboot when nothing else is running. I do not think I have any extensions in nautilus. I think this error appeared for the first time when I was viewing svg in different programs (F-spot, inkscape, firefox), but I am not sure and I do not think it could inflence nautilus.

---

### Post by Darebnicek on 2009-08-03
> **Primefalcon said:**
> also try this from your home
```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

I am not a big fan of this command, but I have already tried this, still nothing.

---

### Post by Primefalcon on 2009-08-04
> **Darebnicek said:**
> I am not a big fan of this command, but I have already tried this, still nothing.
Nor am I but it's saved my but a few times to be honest when i configure the system to hell

---

### Post by indigo42 on 2009-08-24
Mine started acting funny a couple of days ago. Mine crashes when I try to save a download in my home directory. 

So far Firefox and Eclipse will crash, as in die immediately, when browsing in my home directory. I checked for filenames with funky characters, but have found nothing.

I have also noticed that "open containing folder" blows up on the archive manager. You see a window, then it closes in a second.

---

### Post by indigo42 on 2009-08-24
I had renamed a script file to foo.bar. it only had #!/bin/sh in it.

I changed the extention to bak and the problem went away.  

So look in the directory where it is crashing and look for any .bar files.

Good luck.

---

