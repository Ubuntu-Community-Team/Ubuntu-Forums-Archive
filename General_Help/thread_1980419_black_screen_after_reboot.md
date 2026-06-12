---
title: "black screen after reboot"
date: 2012-05-15
forum: General Help
---

### Post by wriordan on 2012-05-15
Hi I'm new to Linux and just recently installed lubuntu on my netbook. I downloaded chrome from google. and installed the package  then after i rebooted my netbook i got a black screen after the lubuntu boot screen. I switched to the terminal(alt+f1) and logged in and rebooted the computer from there after a quick search I've tried 
```
$ startx
```
which brought up a black screen and if i switch back to the terminal i get the following message endlessly

```
no protocol specified
no protocol specified
..
no protocol specified
no protocol specified
..
```

any ideas? as im really lost and don't want to have to reinstall lubuntu + everything else again.

---

### Post by kc1di on 2012-05-15
> **wriordan said:**
> Hi I'm new to Linux and just recently installed lubuntu on my netbook. I downloaded chrome from google. and installed the package  then after i rebooted my netbook i got a black screen after the lubuntu boot screen. I switched to the terminal(alt+f1) and logged in and rebooted the computer from there after a quick search I've tried 
```
$ startx
```
which brought up a black screen and if i switch back to the terminal i get the following message endlessly

```
no protocol specified
no protocol specified
..
no protocol specified
no protocol specified
..
```

any ideas? as im really lost and don't want to have to reinstall lubuntu + everything else again.

have you tried uninstalling chrome ?  
in terminal type this:
```
sudo apt-get purge chrome
```
Then install chromium-browser from the software center or from terminal and see if it will work for you.

---

### Post by wriordan on 2012-05-15
Yes tried that still the same thing.I don't understand it at all.
Edit: except now when i enter startx i get:
```

xinit:connection to X server lost

waiting for X server to shut down ddxSigGiveUp: Closing log
Server terminated succesfully (0). Closing log file.

```

---

### Post by kc1di on 2012-05-15
ok lets try this first.
what video card is the netbook using?
if you don't know please type the following in a terminal and post the results:

```
lspci
``` note l is lowercase L not #1

---

### Post by kuifje09 on 2012-06-19
Sorry, but I hate these errors.
Why?, because its the same as the error from 2 years (about ) ago.
(Some roled the x-version back...)

How can this happen ?

I currently run an update in faile-safe mode. Hope for the best.

It is a waste of time solving the same error again.  ( about  gettime or get time of day ? )

Read your log again,   /var/log/xorg**.log and look at the end.
 X crashes on an error in vdso.

---

### Post by kuifje09 on 2012-06-19
Maybe it can help you... I did the update and now I run the kernel 2.6.38-15-generic.

This obviously installed some other updates, but I can run X again.

Its almost the most important program/service in the system.

Error in Xorg.*.log:
[    26.189]
Backtrace:
[    26.189] 0: /usr/bin/X (xorg_backtrace+0x3b) [0x80f0feb]
[    26.189] 1: /usr/bin/X (0x8048000+0x5df48) [0x80a5f48]
[    26.189] 2: (vdso) (__kernel_rt_sigreturn+0x0) [0xf4340c]
[    26.189] Segmentation fault at address 0x24
[    26.189]
Caught signal 11 (Segmentation fault). Server aborting
[    26.189]

---

### Post by xp15 on 2012-06-19
Can you start startx as root? in the terminal?

here:
```

sudo startx

```

it will ask you for your password. instaed of dot it's unseen to protect it-so you are actually do typing it (:

---

