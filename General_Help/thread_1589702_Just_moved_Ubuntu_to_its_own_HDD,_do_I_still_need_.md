---
title: "Just moved Ubuntu to its own HDD, do I still need a SWAP partition?"
date: 2010-10-06
forum: General Help
---

### Post by PsychedelicWonders on 2010-10-06
Ok at one point I was sharing one HDD with windows 7 & Ubuntu and had a SWAP partition to jump back & forth between the two.

Now I've upgrade to where each will get its own HDD.

So do I still need this 1g swap partition, or can I delete it & add it back to the disk space?

Thanks

---

### Post by andrewthomas on 2010-10-06
It really does not matter if ubuntu is on its own hdd whether you need a swap partition.  It depends on how much RAM you have and whether you use hibernate.

---

### Post by PsychedelicWonders on 2010-10-06
I've got 8g of ram

Should I keep the swap to be safe?  Or you think its not needed?

---

### Post by cgroza on 2010-10-06
Swap is not necessary with all that RAM unless you want to hibernate the computer.

---

### Post by PsychedelicWonders on 2010-10-06
> **cgroza said:**
> Swap is not necessary with all that RAM unless you want to hibernate the computer.

Ok, I dont know if I have it set to hibernate or not, I generally leave my computer on all the time & at some point power savings come on or the screen saver does at some ponit

So is that considered "hibernate"?

---

### Post by PsychedelicWonders on 2010-10-06
I guess I'll keep it... always nice to have another power saving feature

---

### Post by efflandt on 2010-10-07
Power saving features include putting your display in standby, suspend puts your PC in a low power mode that just keeps RAM alive (usually blinking amber power LED), hibernate saves your RAM to swap and shuts down (so it can quickly boot where you left off).  There is also a checkbox to spin down unused hard drives when possible, even while running from another drive.  The screen saver might also dim your display when inactive depending upon how that is set.

I believe it flushes drives before going into suspend, so if you lose power during suspend, you should be able to boot normally.

Hibernate is the only power saving mode that would use swap.  For that they recommend swap size >= RAM size.  I don't know if it really needs that or just enough for active memory (less cache and buffers?).

To check your settings start with System > Preferences > Screensaver, and that has a link to Power Management.

---

