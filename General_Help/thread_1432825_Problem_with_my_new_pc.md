---
title: "Problem with my new pc"
date: 2010-03-18
forum: General Help
---

### Post by echo.whoami on 2010-03-18
i have bought a new pc and i just installed ubuntu 9.10 64bit.
Once i booted in and installed all the updates i reboot it and checked system-monitor giving me 800MB ram usage without having opened any programms except from those that start from default. 

The harware is :
-Amd 965 Phenom II x4 BE
-asrock M3A785GXH/128M
  onboard graphics amd radeon hd 4200
  AMD 785G + SB710 Chipsets
-2xddr3 modules (1GB ram each ,dual channel enabled)

What i get from [COLOR="Red"]dmesg[/COLOR] is (with some highlighted problems that i found):
```
 http://pastebin.com/8Du1SUDt
 
```

Could someone tell me what am i doing wrong and so much memory is in use?

---

### Post by realzippy on 2010-03-18
Ubuntu itself needs it.Everything is ok.

---

### Post by beastrace91 on 2010-03-18
> **realzippy said:**
> Ubuntu itself needs it.Everything is ok.

Ubuntu should be using like 350megs TOPS when you are booted with default applications. Can you open your system monitor and see which application is eating up your RAM?

Also in the future please use [www.pastebin.com](www.pastebin.com) to post just long terminal outputs.

Regards,
~Jeff

---

### Post by plucky on 2010-03-18
> Also in the future please use [www.pastebin.com](www.pastebin.com) to post just long terminal outputs.

Or put [noparse]```

```[/noparse] blocks around it instead of [noparse]> [/noparse] blocks.

Try it you will like it.

Good Luck

---

### Post by echo.whoami on 2010-03-18
There is no application that consumes so much ram in system-monitor. the bigger firefox with 80MB. Do you think it's a problem with the hardware or with the ubuntu? Where should i get a list with the compatible hardware for linux or troubleshooting problems like memory leaking?

---

### Post by beastrace91 on 2010-03-18
> **echo.whoami said:**
> There is no application that consumes so much ram in system-monitor. the bigger firefox with 80MB. Do you think it's a problem with the hardware or with the ubuntu? Where should i get a list with the compatible hardware for linux or troubleshooting problems like memory leaking?

Could you try booting from a LiveCD and see if it eats up this much memory as well? This will tell us if it is an issue with your install or your hardware setup.

Regards,
~Jeff

---

### Post by linden940 on 2010-03-18
hmmm use a 32bit system.....i think the 2gb of ram is a bit to low for a 64bit....

from what i hear...to run 64bit smoothly..u need around 4gb of ram

---

### Post by echo.whoami on 2010-03-18
When i boot up livecd the memory is about 250. Now that i booted again to my install the memory is 285MB, but the problems that i highlighted in the pastebin are still there with dmesg.

---

### Post by linden940 on 2010-03-18
like i had said...u should try the 32bit

---

