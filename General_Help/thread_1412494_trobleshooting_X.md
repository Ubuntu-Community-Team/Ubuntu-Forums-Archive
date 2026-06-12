---
title: "trobleshooting X"
date: 2010-02-21
forum: General Help
---

### Post by goslings on 2010-02-21
Used 9.10 for months without issues
Today it booted up in low resolution for some reason ?!?!
Played around a bit with display - which now it cant reconise
Now only boot up to the black screen with login prompy
tried sudo /ect/init.d/gdm start 
No joy always go into login screen with black background 
(thought I had posted this yesterday ut cant locate it)
Anyone any thoughts ?
Ian - thanks

---

### Post by goslings on 2010-03-15
bounced as still broke and no trplies
any help much appreciated as miss my 9.10

---

### Post by pbrane on 2010-03-15
Have a look at /var/log/Xorg.0.log. After logging in you can type
```

more /var/log/Xorg.0.log

```
look for (EE) or (WW) on the left, those are errors and warnings. There might be a clue as to why your X server is failing to start.

Are you using nvidia proprietary drivers? 

You can always try
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

```
this will rename your existing xorg.conf file. You don't need one to run X, unless you are using a proprietary driver. But this should get you back to low res mode.

---

### Post by goslings on 2010-03-16
> **pbrane said:**
> Have a look at /var/log/Xorg.0.log 
Attached 

> Are you using nvidia proprietary drivers? 
I used to use 173.... and even had all the fancy compiz stuff under 8.04, but this seems now all removed with 9.10

> try sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
 But this should get you back to low res mode.
:KS:KS:KS:KS:KS
It did - oh many many thanks 
I see from the log that 173... drivers will no longer work ?
173... worked for 8.04 & 9.10 including all compiz and avant 
why not now ?
any ideas much appreciated

Many thanks for you help been ](*,) for the past 3 weeks

---

### Post by pbrane on 2010-03-16
Have you tried envyng? It's in the repos and will install a later nvidia driver for you.
I use the latest driver from the nvidia website, but it takes a little work to make it update for ever new kernel. Here is a link I loosely followed to install the driver:
[http://ubuntuforums.org/showthread.php?t=1125400]("http://ubuntuforums.org/showthread.php?t=1125400")
But envyng is easier.

It looks like you meant to attach the Xorg.0.log file. It's not.

---

### Post by goslings on 2010-03-17
> **pbrane said:**
> Have you tried envyng?
Never came across this - I'll look into it (as the other thread is 300+ long - ouch)

> It looks like you meant to attach the Xorg.0.log file. It's not.
Opps sorry, it is at home and I'm away all week 
regards

---

