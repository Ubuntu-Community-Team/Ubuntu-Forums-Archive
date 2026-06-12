---
title: "Ubuntu boot problem"
date: 2010-10-30
forum: General Help
---

### Post by blondyman1503 on 2010-10-30
Ubuntu wont start anymore. I get to the grub bootloader screen, and i can choose which to boot into. But if i choose the one to bring me into Ubuntu the boot screen comes up and it freezes like that. I tried it again and pressed ESC to see what was happening and it was stopping when it got here, ```
Starting TiMidity++ ALSA midi emulation...
``` After it gets to that it doesn't do anything else.
I tried booting into the recovery mode. A bunch of text scrolled down just like when i usually go into there. But this time after all that went by the screen just went black and didnt do anything else.
I tried booting into the LiveCD but i couldnt figure out what to fix...


Also when i was in the LiveCD i tried going into my home folder but all that was in it were 2 thing. One called "Access your private data". It had the icon for an excutable but when i click on it nothing happens. The other one was a text file that said: ```
THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.

From the graphical desktop, click on:
 "Access Your Private Data"

or

From the command line, run:
 ecryptfs-mount-private
```What should I do? Is there anyway to backup my ubuntu files using this: ```
http://ubuntuforums.org/showthread.php?t=35087
```

---

### Post by P4man on 2010-10-30
About that last link: no. Its rarely a good idea to follow a 5 or 6 year old howto, and in this case it wont help you at all as it seems you encrypted your home folder. I cant help you with recovering that (not because its impossible, I just have never used it). Although from what you posted, the obvious thing to try is open a terminal and type in

```
ecryptfs-mount-private
```

(perhaps prefixed with 'sudo')

As to the nonbooting install; if safe mode fails then thats not good. Perhaps from the live session you can browse to /media/yourharddisk/var/log and check some logfiles, like dmesg and see where the boot process chokes on?

---

