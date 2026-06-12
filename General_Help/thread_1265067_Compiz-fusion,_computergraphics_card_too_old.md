---
title: "Compiz-fusion, computer/graphics card too old?"
date: 2009-09-12
forum: General Help
---

### Post by holycow131415 on 2009-09-12
Hello all,

I saw some cool videos of linux with compiz fusion installed. I tried to install and run it, but it says no whitelisted driver found. I have uninstalled it because i just think my system is too old. I have 256 ram, penti 3 dell inspirion 4000. the card is ATI Technologies Inc Rage Mobility M3 AGP 2x (rev 02) which uses the driver r128.

Like i said it is uninstalled because a fix i found didnt work, and required me to configure my xorg.conf file, which is already hand modified to give me 1024/768 res. so when i went to do the fix, it messed up the file so i had to refind the resolution fix again lol. So i dont really want to go around messing with it again.

Is there another program or packet that would work with my configuration?

---

### Post by harrismh777 on 2009-09-13
hi,
check out this page

[https://wiki.ubuntu.com/HardwareSupport](https://wiki.ubuntu.com/HardwareSupport)

Also, do some google searches for your graphics card and see what you can
find regarding "linux friendly" entries for your hardware.

In general, no your machine is *not* too old.  You may have to read the doc on making xorg work with your monitor and graphics card... usually its not too difficult to make things work...

---

### Post by holycow131415 on 2009-09-13
well like i said, it is supported and uses the r128 driver.

---

### Post by CatKiller on 2009-09-13
> **holycow131415 said:**
> I tried to install and run it, but it says no whitelisted driver found.

What happens if you run ```
SKIP_CHECKS=yes compiz
```

> so when i went to do the fix, it messed up the file so i had to refind the resolution fix again lol.

It's generally good practice to make a backup copy of important files before you edit them so that you only have to copy your backup back if you want things back the way they were. In fact, the system does this automatically for you, by creating a copy whose name ends with ~.

---

### Post by holycow131415 on 2009-09-13
OMG, that command really screwed up my desktop. I no longer have minimize, maximize, or x buttons anymore. i cannt move my windows around, and my windows tweak manager does not load anymore. Please  HELP!!

ive already reinstalled xfce, and uninstalled compiz..

---

### Post by CatKiller on 2009-09-13
> **holycow131415 said:**
> OMG, that command really screwed up my desktop. I no longer have minimize, maximize, or x buttons anymore.

Don't panic. That just means that you haven't got a window decorator running.

> 
ive already reinstalled xfce, and uninstalled compiz..

Oh. Too late...

I understand that something like ```
gtk-window-decorator --replace
```will work in xfce.

---

### Post by holycow131415 on 2009-09-14
i had to start the windows manager in terminal to start it again. the demon wasnt started for some reason.

---

### Post by holycow131415 on 2009-09-14
btw does that mean i was close to getting compiz working?

---

### Post by CatKiller on 2009-09-15
> **holycow131415 said:**
> btw does that mean i was close to getting compiz working?

Probably.

---

