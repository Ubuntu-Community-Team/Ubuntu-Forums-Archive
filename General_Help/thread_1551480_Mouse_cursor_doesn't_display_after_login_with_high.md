---
title: "Mouse cursor doesn't display after login with high resolution"
date: 2010-08-12
forum: General Help
---

### Post by fai1224 on 2010-08-12
Version: Ubuntu 10.04 Desktop

Problem:
When I change the resolution higher (e.g. 1920x1080),
mouse cursor disappear, until I open the terminal / Ctrl+Alt+F1 (~F6), or run other applications.
But the main problem is, every time after login, the cursor will disappear
(as I know that, before the login, the resolution is 800x600 60Hz, after login, the resolution will be adjusted according to the setting)
So, anyone know how to fix this problem?

I have searched many related posts before,
some of them told me to upgrade the driver, but it didn't help and become worse (cannot boot up, need to re-install ubuntu)
and some of them told me to modify the xorg file, it didn't help, too. (as xorg.conf doesn't exist and I have tried to create one to do the modification, but didn't help)
Any other solution?

---

### Post by dino99 on 2010-08-12
might be a theme issue, check with an other one (system prefs appearance)

---

### Post by fai1224 on 2010-08-12
> **dino99 said:**
> might be a theme issue, check with an other one (system prefs appearance)
Theme is also related? I will try it tomorrow.
Any other solutions?
Or does anyone know what is the command line / script to let the mouse cursor appear?

---

### Post by fai1224 on 2010-08-12
> **dino99 said:**
> might be a theme issue, check with an other one (system prefs appearance)
It doesn't help

---

### Post by deadlytackler on 2011-05-04
> **fai1224 said:**
> Version: Ubuntu 10.04 Desktop
 
Problem:
When I change the resolution higher (e.g. 1920x1080),
mouse cursor disappear, until I open the terminal / Ctrl+Alt+F1 (~F6), or run other applications.
But the main problem is, every time after login, the cursor will disappear
(as I know that, before the login, the resolution is 800x600 60Hz, after login, the resolution will be adjusted according to the setting)
So, anyone know how to fix this problem?
 
I have searched many related posts before,
some of them told me to upgrade the driver, but it didn't help and become worse (cannot boot up, need to re-install ubuntu)
and some of them told me to modify the xorg file, it didn't help, too. (as xorg.conf doesn't exist and I have tried to create one to do the modification, but didn't help)
Any other solution?
 
Mine is also the same issue, Reinstall Ubuntu 10.04.2 yesterday. However problem rtemain same.
Any Linux guru care to enlighten us on the issue?:confused:

---

### Post by deadlytackler on 2011-05-04
> **fai1224 said:**
> Theme is also related? I will try it tomorrow.
Any other solutions?
Or does anyone know what is the command line / script to let the mouse cursor appear?
 
Way around is press Ctrl+Alt+T and type mouse, mouse will appear, however you have to do it every time you reboot.
 
Only some Linux Guru can save our soul........also trying to find ways to invoke Linux God as many times our prayers go unnoticed.

---

### Post by AfrikaDietmar on 2011-12-30
Hi,

I was having the same problem. This > press Ctrl+Alt+T and type mouse helped to get the mouse back and figure out a solution. I did the following, went on SYSTEM > PREFERENCES > MONITOR and changed my refresh rate from 75 back to 60. Then my mouse pointer stayed even after reboot. Maybe this will help some. 

> Only some Linux Guru can save our soul........also trying to find ways  to invoke Linux God as many times our prayers go unnoticed.     :KS thats the way to go! Keep the faith :) ...the invocation, he can come disguised :evil:  :popcorn:

---

