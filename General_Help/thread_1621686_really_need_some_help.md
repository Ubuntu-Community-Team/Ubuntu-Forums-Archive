---
title: "really need some help"
date: 2010-11-14
forum: General Help
---

### Post by azi_linux on 2010-11-14
hi everyone! i am a brand new user to linux (yay) and am loving it, feeling all excited i thought i'd change my mums OLD laptop she uses to learn computers to linux since it would be faster. now here is where all the problems start...
tried many times to create a 10.10 cd but they all failed, my comp? my cds? w/e.
got hold of a friends cd with 8.04, installed, now tried to do all updates, wouldn't connect to net using wireless usb and doesn't recognize any usbs at all, took out ethernet from ps3 and put in laptop, still nothing. floppy drive is broken.... i know its getting ridiculous now... any help would be appreciated :)
specs:
model = n30n3-14
ram   = probably 16MB
i dont knkow where to find out more info on linux...

tried hardware testing, said internet connection fully established but i cant connect?

thanks guys

---

### Post by sikander3786 on 2010-11-14
Hi. Welcome to the forums :popcorn:

> ram = probably 16MB

Ubuntu will never run on that amount of RAM.

However, regarding you queries, I would recommend that instead of going through all that hassle of updating and all that, it would be just better to install 10.04 and 10.10. What issues were you getting with the newer versions? It would be better if we try and solve those issues with the latest realeases.

Your 8.04 is working, right? We can get your hardware specs from that.

Go to Applications > Accessories > Terminal and post the output of

```
free
```

```
sudo lshw
```

Try to wrap your output with proper code tags # from the post menu to make it easy to read.

BTW, are you sure your Laptop's USB ports are not damaged?

---

### Post by azi_linux on 2010-11-14
thanks for reply. usb ports definitely not damaged since just before linux, windows was used with wifi :)

free command
```
                    total   used   free   shared   buffers   cached
Mem:               239424  235644  3780      0      4572     65036
-/+ buffers/cache:         166036  73388  
Swap:              465844  36544   429300
```

for the lshw command, can i ask what info you want from it, since it has a REALLY LONG list, i'll list the main parts from it.
```
CPU
pentium 3
size: 933MHz
capacity: 1GHz

MEMORY
description: system memory
size: 256MiB
capacity: 384MiB
  bank 0
  descr: DIMM DRAM Synch
  size: 128MiB
  bank 1 *same as bank 0
```

can you tell me what would be an easy linux Os to use then?
thanks again

---

### Post by sikander3786 on 2010-11-14
Well... You seem to have 256 MB RAM and 1 GHZ processor. They are just too low for regular Ubuntu.

You might want to try Lubuntu, a light weight Ubuntu fork.

[http://lubuntu.org](http://lubuntu.org)

PeppermintOS?

[http://peppermintos.com/](http://peppermintos.com/)

This thread might help you decide.

[http://ubuntuforums.org/showthread.php?t=1590614](http://ubuntuforums.org/showthread.php?t=1590614)

---

### Post by azi_linux on 2010-11-14
hmm, thanks, im looking into it right now, but if you can, what are the main differences?

---

### Post by Hippytaff on 2010-11-14
Lubuntu uses Lxde as the desktop thing, so it's lighter, I have it on my battered old desktop.

this might be worth a read - [http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments](http://en.wikipedia.org/wiki/Comparison_of_X_Window_System_desktop_environments)

---

### Post by sikander3786 on 2010-11-14
> **azi_linux said:**
> hmm, thanks, im looking into it right now, but if you can, what are the main differences?
Difference for what?

If you mean the difference between Ubuntu and Lubuntu, Ubuntu comes with Gnome dektop environment, Kubuntu with KDE, both are resource hungry but more pleasant and lots of eyecandy. Lubuntu comes with LXDE which is a lightweight DE, not that much resource hungry.

Different Linux distro have different desktop environments, different set of apps, default services. You can simply Google "Lubunut vs Ubuntu" or "Lubuntu vs Kubuntu".

---

### Post by azi_linux on 2010-11-14
sorry, meant between lubuntu and xubuntu, but after reading up everywhere im going to go with lubuntu, thanks for all the help guys! after i buy a new desktop i will be solely on linux :D
......expect noob questions at that time...

---

### Post by Hippytaff on 2010-11-14
Look at my beans...mostly questions :-)

---

