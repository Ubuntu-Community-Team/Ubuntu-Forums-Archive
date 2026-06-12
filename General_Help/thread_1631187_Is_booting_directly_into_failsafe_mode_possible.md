---
title: "Is booting directly into failsafe mode possible?"
date: 2010-11-26
forum: General Help
---

### Post by TehGoose on 2010-11-26
Hi, this is my first post here. I'm not really sure of the rules or categories but I couldn't see one more relevant than this.

I just installed Ubuntu 10.10 on a machine with a dodgey graphics card. This machine will break on normal graphics mode but run fine in failsafe graphics mode. I need this machine to be able to be controlled remotely and this is where the problem comes in.

If this machine is being controlled remotely, it may need to be rebooted remotely. Rebooting it into failsafe mode at the moment consists of two prompts: one to put it into failsafe, and the other to "keep it for one session". Does anyone know how to reconfigure Grub or whatever else so it will automatically go into Failsafe Graphics mode without any user interaction?

(BTW, where it asked me to "keep for one session" or "reconfigure now", I clicked reconfigure and it didn't do anything. So I need to do it manually)

Thanks in advance :)

---

### Post by dino99 on 2010-11-26
let us know if its a fresh install or a dist-upgrade

then which graphic card/chip it is

---

### Post by TehGoose on 2010-11-26
> **dino99 said:**
> let us know if its a fresh install or a dist-upgrade

then which graphic card/chip it is
It's a fresh install from a USB stick (the DVD drive is also broken). The graphics card is an nVidia GeForce Go 7950 GTX, but it is old and definitely broken. This is in a Dell XPS M1710 btw. I don't need the graphics working, just for the machine to run, and run remotely.

Thanks for the reply :)

---

### Post by TehGoose on 2010-11-26
It's ok. I have it solved now. A very simple solution actually. I just uninstalled all nVidia drivers so now it can't use the graphics to the extent that it breaks :)

Thanks for putting the idea in my head :D

---

### Post by dino99 on 2010-11-26
ive searched about booting in recovery by default, but its not documented. So why not create/modify xorg.conf to set driver=vesa

---

