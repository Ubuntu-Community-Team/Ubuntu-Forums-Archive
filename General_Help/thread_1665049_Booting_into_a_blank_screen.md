---
title: "Booting into a blank screen"
date: 2011-01-11
forum: General Help
---

### Post by 300Z on 2011-01-11
I had a problem with my system today when I came home and unlocked the screen and the single program I had left running had crashed and so did AWN, I restarted the system and it just goes to a blank screen just before it got to the login and does nothing. I reinstalled the system and reinstalled the ATI drivers downloaded from the ATI website just like I had previously (had problems with the Ubuntu drivers in the past) and rebooted the system and got the same blank screen... :(
Now I'm on my second system reinstall of the night but haven't installed the ATI drivers yet, but I need them to set up my dual screen gig.

Any ideas or tips about what may be happening?

---

### Post by 300Z on 2011-01-12
Any1? :(

---

### Post by NT4usB on 2011-01-12
Lots of ideas... too many to list.
I'll start with a basic 'gotcha' I ran into recently.

I use the nvidia binaries, from nvidia, but could be related to the third party video driver in general.

After a few days and startups, got a black screen at boot.
 
Turned out, fsck chose that time to check the HDD's and because of some quirk in the latest Ubuntu releases, video doesn't load before the checking begins.

None of the terminals worked (Ctrl+Alt+F1) but I could tell the box was alive since the Numlock light responded.

Found out after banging on combinations of Ctrl+Alt+Backspace which interrupted the fsck... and corrupted the boot process, but got me a screen. 

Then I could look at a log and see it was fsck hanging it up.

Now, I just wait 20-30 minutes for the HDD check to complete and I get a login screen.

There are many, many other things that could go wrong, and ways to fix them. Reinstalling is way at the bottom of the list though.
Does Ctrl+Alt+F1 get you to a TTY with a login prompt?

---

### Post by Johannes Eva on 2011-01-14
Same thing with Ubuntu 9.10 - normal boot and then, freezes on black screen.

Any idea ?

---

### Post by 300Z on 2011-01-14
After two reinstalls with the same results I gave up in the mean time. After installing the the ATI drivers the system just boots to a blank screen right before it reaches the login screen and then it stops there.

Not sure if by having a separate partition for /home is contributing to this by keeping all my settings after the reinstall.

---

### Post by janaro on 2011-04-05
I'm not much of an expert but I think that to do with your drivers or the open source drivers....

The experts out there might be able to tell me if the following helps you:
```
sudo dpkg-reconfigure xserver-xorg
```I have a similar problem but sometimes it works and sometimes it doesn't:
Some cases I get a blank screen and other I get the user account and a message at the top saying that the power management has failed...

Can anyone help?


I have tried restoring the management power with:
```
sudo dpkg-reconfigure gnome-power-manager
```Restoring the GPU drivers:
```
sudo dpkg-reconfigure xserver-xorg
```Thanks for reading!

---

