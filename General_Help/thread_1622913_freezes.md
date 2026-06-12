---
title: "freezes"
date: 2010-11-16
forum: General Help
---

### Post by csckid on 2010-11-16
I have installed ubuntu 10.04 on my pc. I'm using 2 OS xp and ubuntu 10.04. The problem is during startup of ubuntu it freezes. Let say after 15 sec-1min in between ubuntu hangs. I have reinstalled the CD again, ran ubuntu with liveCD still the problem persist. 
Few months back I tried to install 9.04 or 9.10. Even in that my pc froze. However, 8.10 ran properly.


My fried installed the same iso file that I have, but with different CD, his ubuntu worked perfectly.


Why is that so?

During installation I assigned mount point: / and EXT4

---

### Post by ajgreeny on 2010-11-16
It is difficult to help with no information about your hardware; laptop, desktop, what graphic card, how much ram? etc etc.

Let us know more and you may get suggestions on how to proceed.

---

### Post by csckid on 2010-11-16
> **ajgreeny said:**
> It is difficult to help with no information about your hardware; laptop, desktop, what graphic card, how much ram? etc etc.

Let us know more and you may get suggestions on how to proceed.


hardware: core 2 duo 2 GHZ, 1GB Ram, 128MB AGP, built in intel graphics card. allocated 10GB for ubuntu.

---

### Post by gandaran on 2010-11-16
> **csckid said:**
> I have installed ubuntu 10.04 on my pc. I'm using 2 OS xp and ubuntu 10.04. The problem is during startup of ubuntu it freezes. Let say after 15 sec-1min in between ubuntu hangs. I have reinstalled the CD again, ran ubuntu with liveCD still the problem persist. 
Few months back I tried to install 9.04 or 9.10. Even in that my pc froze. However, 8.10 ran properly.


My fried installed the same iso file that I have, but with different CD, his ubuntu worked perfectly.


Why is that so?

During installation I assigned mount point: / and EXT4
Hi
does running the live cd work?
I had the same problem on my netbook, 8.04 would run fine but newer linux kernels would freeze all the time, the fix for my netbook was just to update Bios.
I don't know if in your case updating Bios would resolve the problem but you can try it.

---

### Post by mirearts KING SUNNY on 2010-11-16
There maybe some peripherals (such as memory, graphics..) and your BIOS setup that need to be checked. Detach them clean for dust and replace. Restore your BIOS settings to its default. Try to install Uuntu on another drive to see if it freeses.

---

### Post by csckid on 2010-11-16
> **gandaran said:**
> Hi
does running the live cd work?
I had the same problem on my netbook, 8.04 would run fine but newer linux kernels would freeze all the time, the fix for my netbook was just to update Bios.
I don't know if in your case updating Bios would resolve the problem but you can try it.

What change did you do to your bios? I'm using destop pc.

---

### Post by gandaran on 2010-11-16
> **csckid said:**
> What change did you do to your bios? I'm using destop pc.
I just downloaded the new BIOS software from the Toshiba website for my Toshiba netbook and run the .exe file in windows xp, thats all, after this there was no problem running any Linux version. 
Go to your PC brand website and see if theres a BIOS update for your PC model available and if you have windows installed in the PC it should be easy to update the BIOS.

---

### Post by csckid on 2010-11-21
> **gandaran said:**
> I just downloaded the new BIOS software from the Toshiba website for my Toshiba netbook and run the .exe file in windows xp, thats all, after this there was no problem running any Linux version. 
Go to your PC brand website and see if theres a BIOS update for your PC model available and if you have windows installed in the PC it should be easy to update the BIOS.

I'm not using any brand PC like dell, hp.... and don't have any idea about where to download bios from. 

Isn't there any other way to solve. I have installed 8.10. It runs smoothly without hang. But it doesn't restart properly. It gives a black screen and nothing happens.

tried this didn't work
sudo /etc/init.d/gdm restart

---

