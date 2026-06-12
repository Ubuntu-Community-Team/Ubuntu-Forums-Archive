---
title: "Install Proprietary Drivers Problem"
date: 2011-09-15
forum: General Help
---

### Post by sublimnalxx on 2011-09-15
I installed the proprietary drivers on Ubuntu for my graphics card twice now. The first time I installed, I  installed the drivers recommended by Ubuntu. After the reboot I would be taken to the Ubuntu splash screen and then it would disappear, revealing info about the processes and it would stay stuck there.

I decided to reinstall and this second time I installed the version 173 drivers. Now the splash screen comes up quickly and then my monitor turns blank and says "no signal" as if it were not connected to the computer. What do I do?

---

### Post by MG&amp;TL on 2011-09-15
What version of Ubuntu and what card? I get a horribly similiar thing to this with my Nvidia GeForce FX5200 and anything with Unity. (11.04 onwards)

---

### Post by sublimnalxx on 2011-09-15
Ubuntu 11.04 and some Nvidia GeForce  card. I'm not exactly sure on which model since I can't seem to get past the splash screen anymore without having to reinstall (again).

---

### Post by coffeecat on 2011-09-15
This is how you can find out which model Geforce you have without a GUI. Select recovery mode from the grub menu and at the secondary menu, choose drop to root shell (or root prompt - I can't remember the exact words). It doesn't matter whether you choose with networking or not. You will be presented with a # prompt. You have full root privileges so be careful what you type. Now run this command:

```
lspci | grep VGA
```

Make a note of the output and post it. I won't be able to help you further because I have abandoned nvidia cards in favour of ATI. (I like to swim against the tide. :wink:) Apart from the 5200 that MG&TL mentions, I believe there are problems with some of the 7??? series. Anyway, hopefully someone will be able to help you when you know which your particular GPU is.

---

### Post by sublimnalxx on 2011-09-15
When I boot, I don't get a choice to boot in recovery.

EDIT:

I take that back. After rebooting a few times it came up. 
I get 2 graphics cards from that command.

GeForce 8200
GeForce 9300 

All I want to do is revert the update I did at the very least. Any way I can do that without reinstalling?

---

### Post by sublimnalxx on 2011-09-16
> **MG&TL said:**
> What version of Ubuntu and what card? I get a horribly similiar thing to this with my Nvidia GeForce FX5200 and anything with Unity. (11.04 onwards)

I have a solution that may work for you. I got them to install correctly, I don't even know how, they just worked. here's what I did.

When I installed the proprietary drivers and my screen turned blank, I booted in recovery mode, and booted with low graphics on. Then what I did was go to the proprietary drivers again, removed the proprietary drivers, rebooted in normal mode and re-installed them. Somehow, some way they installed the way they should and worked. However, I also came across this link which explains why you may be having problems.

```
https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia
```

i would have a quick read and see if any of the problems and / or solutions applies to you.

---

### Post by MG&amp;TL on 2011-09-16
Sorry, been there done that, my compute hangs accessing recovery mode. Pleased you got yours done though.

---

### Post by coffeecat on 2011-09-16
> **sublimnalxx said:**
>  
I get 2 graphics cards from that command.

GeForce 8200
GeForce 9300 

All I want to do is revert the update I did at the very least. Any way I can do that without reinstalling?

That's very interesting. Do you have two graphics cards installed, or do you have onboard nvidia graphics plus a graphics PCIe card? Whichever, it must be that both are enabled in the BIOS for them to appear in the output of lspci. Most BIOS's, in my experience, will auto-disable onboard graphics when you fit a PCIe card, but some don't. It could be that the presence of two GPUs is confusing things. Try disabling the graphics you are not using in the BIOS. Also make sure that your VGA/DVI cable is plugged into the appropriate one.

---

