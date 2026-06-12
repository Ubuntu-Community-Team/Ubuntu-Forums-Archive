---
title: "ubuntu is running in low graphics mode"
date: 2011-01-08
forum: General Help
---

### Post by owners4life5 on 2011-01-08
hello,

i recently had a hard drive on a computer (not to be obvious), and i fried the computer. you may ask "well why did you do that?" well, simply because i had accidentally bumped and switched to 220 volts, rather than keeping it at 115 like a sane individual... (;

anyway, i got a new computer, swapped the hard drive. when i go to boot into ubuntu though, it gives me the following error:

```
**Ubuntu is running in low-graphics mode**

The following error was encountered. You may need to update your configuration to solve this.

(EE) No devices detected.
```

and so that is that. I also have XP on this hard drive, and it works almost better than it did on my old one, surprisingly. all i have to do now for it to be labeled as efficient, is to get some RAM.

But anyway, what can I do about the error message? I tried booting into recovery, running dpkg from the list of options, and it did a couple of things, me thinking it would fix my problem...but it didn't. so what exactly can i do?

thanks in advance,

---

### Post by owners4life5 on 2011-01-08
i know there tends to be a 24hr limit, but this is kinda urgent.

---

### Post by amsterdamharu on 2011-01-09
You could try to rename the xorg.cfg. 
Log out and then press control + alt + F1 then log in and issue the following commands:
```
sudo service gdm stop
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.old
sudo service gdm start
```
Note that the X in X11 is upper case

Now when you log in maybe it will detect the videocard. If not you can try rebooting.

To see what videocard you've got and what drivers are loaded you could post the output of the following commands:
```
sudo lshw -C video
lsmod | grep agp
```

---

### Post by owners4life5 on 2011-01-09
this fixed it. thank you very much, goodsir (:

---

