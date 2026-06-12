---
title: "Ubuntu + XBMC Questions."
date: 2011-07-18
forum: General Help
---

### Post by nollkoll on 2011-07-18
Hi guys, Ubuntu amateur on-and-off user since Breezy here.

I recently bought a computer and the plan was to mainly use it for XBMC and configure my system to start XBMC as a replacement for GDM, however the only thing i've managed to do is install XBMC from their repo, and break grub while following some less-than-documented guides on how to add a XBMC splash-screen to replace the standard ubuntu boot screen.

TL;DR this is what i want to acomplish:
[LIST]
[*]Start XBMC without GDM
[*]Use XBMC logo as boot-screen and screen before the system shuts down
[*]Be able to start GDM on the side of XBMC(On/in another X screen/session?)
[/LIST]

These are the guides i've followed on-and off, in some of them the files im supposed to edit dont exsist so i just "opened" the files in VIM in a terminal and then did a !wq.

[http://forum.xbmc.org/showthread.php?t=41739](http://forum.xbmc.org/showthread.php?t=41739) (This didnt work/the XBMC session was amongs the list of sessions avaible, but when i tried to use it the screen went black for a few seconds then im back at the login screen)

[http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide#Autostart_XBMC_.28optional.29](http://wiki.xbmc.org/index.php?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu,_a_Step-by-Step_Guide#Autostart_XBMC_.28optional.29) I did most of that (Except for the SVN thingy as i didnt know what it was), The first option for autostarting didnt work as i couldnt find XBMC as a session when i was logged out.

I'dd be really grateful if anyone could help me out, some pointers on what to download and possibly the commands if its not too dummy-friendly in the level of complexity.

---

### Post by sanderd17 on 2011-07-18
how about installing the xbmc live CD? [http://wiki.xbmc.org/index.php?title=XBMC_Live](http://wiki.xbmc.org/index.php?title=XBMC_Live)

This is stripped down Ubuntu, with xbmc preconfigured.

---

### Post by nollkoll on 2011-07-18
I'll certainly try that when i get back home, is it possible to access GDM with the XBMC-live dist tho? and will most stuff work out-of-the-box? (aside from drivers possibly)

---

### Post by sanderd17 on 2011-07-18
No, gdm is not installed if I remember correctly. But when you press CTRL+ALT+F2, you are in an Ubuntu terminal, and you can install what you want with apt-get. e.g.

```

sudo apt-get install gdm

```

On the other hand, I don't think it is possible to use GDM from xbmc out. I believe the easiest would be to have one XBMC installation and another normal Ubuntu with a graphical environment to work on your computer. So that you can select them on boot time.

---

### Post by nollkoll on 2011-07-18
Its kinda funny, for some weird reason i didnt think about the dualbooting, it toally slipped my mind :D

I'll dualboot ubuntu and XBMC (and possibly win7 if for some weird reason i need that, you never know).

Thanks alot for the help!

---

