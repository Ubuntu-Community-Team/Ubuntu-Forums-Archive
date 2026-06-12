---
title: "Black screen after booting"
date: 2010-11-22
forum: General Help
---

### Post by Ayuniverse on 2010-11-22
Hi,

I'm new using Ubuntu desktop and I made a mistake while reading a tutorial on shell. I used the bind ctrl + alt + Fx (in this case, F6) and I didn't know how to come back to my original desktop after that. So I did a hard reboot :oops:. Since, after booting I see the loading screen with Ubuntu writen on a purple background, but after that I get a black screen and I cannot type or do anything. 

I tried to log in in "safe mode" (or something like that) and it worked but I got a low screen resolution of course and after rebooting in normal mode it still doesn't work.

Thank you if you can help me ;)

---

### Post by pawhtiobo on 2010-11-22
Hi :)

It seems that your display configuration is for some reason wrong, you can try to boot in "recovery mode" (safe mode) and run in the command:
[B]
sudo dpkg-reconfigure xserver-xorg
[/B]
to reconfigure your X.

What version of Ubuntu are you running? Which VGA card are you using?



see ya....

---

### Post by Ayuniverse on 2010-11-22
Thank you for your answer ;)

Nothing's been displayed when I ran in this command, I just got the prompt back, is it normal ?

Anyway, it still doesn't work :(

I think that must be the version of Ubuntu i'm running : Ubuntu 4.4.3-4ubuntu5

I'm using a XFX Radeon HD 5870 1Go video card

---

### Post by Ayuniverse on 2010-11-22
Solved ;)

I just removed the driver, took the latest version and installed it ^^

Should have done this before creating a topic... :oops:

Anyway, thank you for your time ;)

---

### Post by pawhtiobo on 2010-11-23
Nice :guitar:

---

### Post by pawhtiobo on 2010-11-23
> **usman77 said:**
> We have   been getting many new users lately who don't seem to know the finer points of   our rules.


What are you talking about? :)


See ya...

---

