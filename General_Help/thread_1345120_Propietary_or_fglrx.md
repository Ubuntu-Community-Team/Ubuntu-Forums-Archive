---
title: "Propietary or fglrx?"
date: 2009-12-03
forum: General Help
---

### Post by prions on 2009-12-03
I'm currently running Ubuntu 8.10, and its working well for me. My graphics card, ATI X200m is activated and running nicely.

I like to play some games on Wine like Guild Wars and Garrys Mod, but I'm wondering if I should upgrade to 9.10. 

Although 9.10 doesn't support my card, could I still play those games as well with the open sourced drivers? I don't want to upgrade and find out that no games work.

---

### Post by StuartN on 2009-12-03
> **prions said:**
> Although 9.10 doesn't support my card, could I still play those games as well with the open sourced drivers? I don't want to upgrade and find out that no games work.

Of course 9.10 supports that card (works fine in my PC), using the open source driver.

If you want to test a specific game, then boot using the Live CD, install the game and try it. It will not affect your current installation.

---

### Post by prions on 2009-12-03
Alright I'll try that. The reason I want to move up to 9.10 is that 8.10 is horribly slow for me. :/

---

### Post by StuartN on 2009-12-03
> **prions said:**
> Alright I'll try that. The reason I want to move up to 9.10 is that 8.10 is horribly slow for me. :/

You probably will not notice a vast increase in speed with 9.10. It is worth looking at the system monitor while running slow applications to see which resources are limited. I am not a gamer, but I find versions from 8.04 to 9.10 perfectly useable on several systems with similar specifications, although 2 MB ram is definitely a benefit.

I just put a brand-new NVidia graphics card with 512 MB into one 8-year-old machine and the increase in performance is amazing in World of Goo, but not at all noticeable in regular applications.

---

### Post by prions on 2009-12-03
I tried running a game from 9.10, but when I go to mount my other drive, it says "unable to mount, the unclosing drive for the volume is locked."

---

### Post by StuartN on 2009-12-03
> **prions said:**
> I tried running a game from 9.10, but when I go to mount my other drive, it says "unable to mount, the unclosing drive for the volume is locked."

Perhaps you need to install ntfsprogs if the partitions are formatted NTFS?

---

### Post by prions on 2009-12-03
One is nfts (Windows) and the other partition is sda5 (ubuntu 8.10)

I'll try that though.

Edit: I do have ntfsprogs already in synaptic.

---

