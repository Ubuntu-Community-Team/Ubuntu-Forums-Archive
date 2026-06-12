---
title: "[ERROR HELP] SYSTEM &gt; ADMINISTRATION &gt; Synaptic Package Manager &amp; Update Manager"
date: 2010-01-29
forum: General Help
---

### Post by retro_killa on 2010-01-29
When I go to SYSTEM > ADMINISTRATION > Synaptic Package Manager I get this pop up window that says 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

This also happens when I go to SYSTEM > ADMINISTRATION > Update Manager 

How can I get this error to be fixed & working correctly ?

---

### Post by howefield on 2010-01-29
Open a terminal (Applications > Accessories > Terminal) and type

```
sudo dpkg --configure -a
```

---

### Post by LuridCinema on 2010-01-29
Bottom line is an installation or upgrade got interrupted and you need to restart and finish it

---

### Post by retro_killa on 2010-01-29
> **howefield said:**
> Open a terminal (Applications > Accessories > Terminal) and type

```
sudo dpkg --configure -a
```

When I did the aboe like you stated I get this 

```
dpkg: status database area is locked by another process
```

---

### Post by howefield on 2010-01-29
Means you are using another package manager at the same time.

Try rebooting, to be sure nothing else is running, then try the command.

---

### Post by retro_killa on 2010-01-29
> **howefield said:**
> Means you are using another package manager at the same time.

Try rebooting, to be sure nothing else is running, then try the command.

Ah your right this worked after reboot. :KS:KS:KS

---

### Post by howefield on 2010-01-29
Thanks for the update, good to know :)

---

### Post by hunterkasy on 2010-01-29
I had this exact problem tonight, and the code stated above works thanks,  btw, why can't ubuntu auto fix the install that was interupted so it wil always work without user interaction, with termanal

---

### Post by howefield on 2010-01-29
> **hunterkasy said:**
> I had this exact problem tonight, and the code stated above works thanks,  btw, why can't ubuntu auto fix the install that was interupted so it wil always work without user interaction, with termanal

It is an easy fix, however like everything else, it is only easy when you know how (even though the error tells you exactly what's up) :)

There are a few threads on brainstorm.ubuntu.com regarding this topic.

Go ahead and vote it up, it is the least you can do to help make it happen. :)

[http://brainstorm.ubuntu.com/idea/2298/](http://brainstorm.ubuntu.com/idea/2298/)

---

