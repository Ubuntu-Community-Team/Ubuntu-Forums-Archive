---
title: "Wireless keyboard and grub"
date: 2009-08-19
forum: General Help
---

### Post by sacredsunder on 2009-08-19
I recently replaced an old logitech ps2 keyboard with a usb wireless keyboard/mouse combo the logitech mk300. They keyboard and mouse are awesome. But I have a problem getting the keyboard to work in the bios and in the grub bootloader. I have a fairly new motherboard(under2 years old) and I have turned on usb keyboard and mouse in the bios, but the keyboard still does not work.

Long story short, I was wondering if there is a way to have the grub boot loader randomly select between windows xp and ubuntu?
Or if anyone has another unique fix thatd be cool to. Thanks!

---

### Post by pqwoerituytrueiwoq on 2009-08-19
i don't know about random
you can change which boots by default
applications -> add/remove search for grub menu editor

---

### Post by stlsaint on 2009-08-19
once you boot into ubuntu you can select which os grub will boot next...not quite sure what the program is but go into repos and type in grub and you will see a few options there...check them out to find exactly what you are looking for!

---

### Post by sacredsunder on 2009-08-19
so if i do that and my keyboard dosnt work, does it just load windows once, and go back to ubuntu?

---

### Post by sacredsunder on 2009-08-21
yes, no?

---

### Post by bchurchill on 2009-08-21
I don't think we're quite sure what you're asking.  GRUB will load whatever the default is in /boot/grub/menu.lst each time it boots up.  If you need to change it but only Windows is booting you'll need to use a LiveCD and mount your hard drive.

---

### Post by sacredsunder on 2009-08-21
ok, the keyboard does not respond at all. so if in linux i set grub to boot into windows. then windows boots. i shut it down, restart it. then it will keep booting into windows. i have a spare ps2 keyboard that does work, but thats a pretty wicked hassle. i just want a way to alternate between the two when the keyboard dosnt work. later today (after i get some sleep) im going to check and see if the windows bootloader has and better success talking with the keyboard (apparently the logitech mk300 dosnt have linux support) Ill report back if i have any success

long story short, itd be nice to have grub load linux one time, then windows the next time, then back to linux, then windows. and so on, every time it restarts, automatically.(might be asking too much) :(

---

### Post by sacredsunder on 2009-08-21
ok i feel stupid as hell... after contacting both logitech and my motherboard manufacture i figured out what the issue was. for some reason my wireless usb card had something to do with it. i unpluged that and the keyboard works fine now... >.> such a waste of time... pluged the wireless usb card back in and it still works... i think my computer just hates me... thanks for the help anyways everyone

---

### Post by tgeer43 on 2009-08-21
> **sacredsunder said:**
> Long story short, I was wondering if there is a way to have the grub boot loader randomly select between windows xp and ubuntu?Are you sure that you want to *randomly* select Ubuntu or XP? That's pretty bizarre.
Perhaps you meant that you want it to load one or the other? If so, then edit /boot/grub/menu.lst as root (back it up first):
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR=Red]default        0[/COLOR]**
```Hope this helps,

tgeer

---

### Post by Post Monkeh on 2009-08-21
> **tgeer43 said:**
> Are you sure that you want to *randomly* select Ubuntu or XP? That's pretty bizarre.
Perhaps you meant that you want it to load one or the other? If so, then edit /boot/grub/menu.lst as root (back it up first):
```
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR=Red]default        0[/COLOR]**
```Hope this helps,

tgeer

no, he did want to RANDOMLY select them.

his keyboard wasn't working during the grub selection process meaning he was stuck with always booting the default selection.  randomising it would mean that at least he could boot both systems.

but he's fixed his keyboard, so it's all good.

---

### Post by zer010 on 2011-04-03
I just figured this one out for GRUB2 in 10.04. I had this working at one time, but then I lost it.  Apparently, I had to switch to a different USB port on the back of my PC.  I put mine in port 1,  where I had it in port 3.  Hope this helps anyone else that is about to pull their hair out. ^.^d

1 | |   2 | |

3 | |   4 | |

---

