---
title: "Second Graphics Card Not showing"
date: 2010-01-21
forum: General Help
---

### Post by jbird80 on 2010-01-21
I've put a second video card in my computer running 9.10(64-bit) to setup a 3rd monitor. I'm using the following video cards with the 190 driver from nVidia:
    Video Card 0: nVidia GeForce 9500 (PCI express x16)
    Video Card 1: nVidia GeForce 6200 (PCI)

but when i run lspci the second video card isn't seen in the list. The bios is set to automatic detection, and I've seen it work on a identical second system that has windows 7 so I know the bios is capable of running the two cards concurrently. 

I've verified the 190 driver is compatible with the 6200 series and have tested it by setting the bios to use the (PCI) device manually.

Now I've kinda hit a dead end, any suggestions would be appreciated.

---

### Post by hemimaniac on 2010-01-21
I ran into this awhile ago, I solved by simply installing the GFX Cards separately, I mean take the first one out, put the second one in its slot (that will be its home ) and install it, then put both in and everything was fine. I realize not the super techy fix you were expecting, but something to try?

---

### Post by jbird80 on 2010-01-22
Thank you hemimaniac, but no dice. the second graphics card still isn't seen when the primary card is inserted.

---

### Post by realzippy on 2010-01-22
> **jbird80 said:**
> Thank you hemimaniac, but no dice. the second graphics card still isn't seen when the primary card is inserted.


...and when it is **not** inserted??

---

### Post by jbird80 on 2010-01-22
> **realzippy said:**
> ...and when it is **not** inserted??

the pci card works fine... I've swapped it with a co-workers 8400gs card and it worked.

although the GeForce 6200 is supported by the 190.53 nVidia driver I guess its different enough for the system not to like it.

---

### Post by ibuclaw on 2010-01-22
```
lspci
```
That will list all PCI devices.

Posting the output here will give us an indication of whether or not it's detected.


Regards
Iain

---

### Post by jbird80 on 2010-01-22
Running lspci | grep VGA only display the PCI express card. with only the PCI card in it displays the 6200 information.

---

### Post by ibuclaw on 2010-01-22
Have you considered that BIOS may be preferring one card over the other? Check if there may be an option available to configure otherwise.

Regards
Iain

---

### Post by jbird80 on 2010-01-22
BIOS is set to Automatic, and the only other options are integrated (which is disabled when a external gfx card is added), PCIE, and PCI. 

It looks like its a compatibility issue with the GeForce 6200 series and the GeForce 9400 series, it worked with my co-workers GeForce 8400 series. I've already ordered a GeForce 8400 so now I'm just waiting for it to arrive. chances are it has to do with the driver requirements of the two graphics cards. although they are compatible with the same driver version they seem to be conflicting with each other.

---

