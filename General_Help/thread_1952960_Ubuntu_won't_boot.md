---
title: "Ubuntu won't boot"
date: 2012-04-05
forum: General Help
---

### Post by thedudething on 2012-04-05
I run Ubuntu 11.04 and for some reason it won't boot.

My Ubuntu frequently freezes and I always end up needing to hard reset the computer (probably because I only have 2GB ram). I was trying to run some updates until my computer decided to freeze again, so I tried to hard reset and was going to do the updates in smaller parts. However when I tried to restart, it got to the black screen where it said it was loading the "unattended updates" again. When it get's up to "Starting TiMidity++ ALSO midi emulation", it get's stuck there instead of going further.

Help anyone?

---

### Post by grahammechanical on 2012-04-05
2GB RAM is plenty. I only have 1GB and I do not get freezes like you mentioned. You should look for other reasons for the freezing. But first you need a desktop.

I do not know the answer but you might want to try booting into an earlier kernel or booting into rescue mode and at the command line type 

```
sudo apt-get update && sudo apt-get upgrade
```

Others on the forum may have better advice.

regards

---

### Post by thedudething on 2012-04-05
How do I boot into rescue mode?

---

### Post by kc1di on 2012-04-05
2 Gb is fine.

sound almost like a bad ram stick or HD going bad. 
But that's just a guess.
You can run the memory test and see if it' ram.
sometimes just removing the ram sticks and reseating them helps.

---

### Post by thedudething on 2012-04-05
The freezing isn't what I'm asking about. I'm asking about the fact that my Ubuntu won't load anymore and stops at that black screen. This only started happening after I tried to do some updates and had to do a hard reset because my computer froze.

---

### Post by kc1di on 2012-04-05
> **thedudething said:**
> The freezing isn't what I'm asking about. I'm asking about the fact that my Ubuntu won't load anymore and stops at that black screen. This only started happening after I tried to do some updates and had to do a hard reset because my computer froze.
my suspicions are that you rebooted while the system was processing the new kernel or boot loader. 

When you boot from the boot menu there should be a option for booting in safe mode.
Try that. 
if you can get to a terminal run the following commands
```
sudo dpkg --configure -a
```
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
see if that does it.

---

### Post by thedudething on 2012-04-05
There is no option to go to safe mode. Just two options: Windows 7 and Ubuntu.

---

### Post by kc1di on 2012-04-05
> **thedudething said:**
> There is no option to go to safe mode. Just two options: Windows 7 and Ubuntu.

is this a wubi install?

---

### Post by thedudething on 2012-04-05
Yes, wubi

---

### Post by bcbc on 2012-04-05
Doing hard resets on a wubi install is going to [destroy it]("https://wiki.ubuntu.com/WubiGuide#Warning").
Use Alt+SysRq R-E-I-S-U-B instead.

You probably need to [fsck]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F") it now. Hold down the SHIFT key after selecting Ubuntu and the grub menu should appear, if you want to boot recovery mode. If you do, first hit 'E' on the entry and check the first line. If it says something like 'set gfxpayload' then delete it and hit Ctrl+X to boot.

---

### Post by thedudething on 2012-04-06
I managed to get into recovery mode and ran "sudo dpkg --configure -a" "sudo apt-get update" and "sudo apt-get upgrade"

Still had the same problem when I booted to Ubuntu though. It goes through the "unattended upgrades" and when it gets to "Starting TiMidity++ ALSA midi emulation", it just stops there.

---

