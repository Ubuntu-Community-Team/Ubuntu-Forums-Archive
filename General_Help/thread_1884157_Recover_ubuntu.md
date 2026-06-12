---
title: "Recover ubuntu"
date: 2011-11-20
forum: General Help
---

### Post by QuimNuss on 2011-11-20
After I installed the ATI driver, ubuntu fails to boot and drops to a black screen after showing the splash. I believe the grub is disabled, so I can't go with 'recovery mode' boot.

I haven't succeded into getting to a shell prompt to remove the driver! it's driving me nuts. Even the LiveCD reboots after chosing the option 'Try ubuntu without installing'.

Please help! It's kind of urgent... and I won't resign in re-installing everything and losing the data. :(

---

### Post by dniMretsaM on 2011-11-20
What happens when you boot while holding the Shift key? It should bring up GRUB. If not, you'll need to restore GRUB. If you can't get into a live environment to do that, try a rescue disk like Rescatux or Super GRUB/GRUB2 Disk. And didn't you back up your data?

---

### Post by searchfgold6789 on 2011-11-20
> **QuimNuss said:**
> 
I haven't succeded into getting to a shell prompt to remove the driver! it's driving me nuts. Even the LiveCD reboots after chosing the option 'Try ubuntu without installing'. 
Which version of Ubuntu? Sounds old.

---

### Post by dniMretsaM on 2011-11-20
> **searchfgold6789 said:**
> Which version of Ubuntu? Sounds old.

Oh yeah good catch. I was just thinking 10.04 but come to think of it it doesn't have that old menu. So try booting a LiveCD of a newer version.

---

### Post by QuimNuss on 2011-11-21
Thanks for your comments. I didn't know the grub menu was brought up with the shift key. How could I get to a root prompt from there? The recovery mode ends up at the same point, with a black screen after showing the lines:

Running /scripts/init-bottom ...
Done.

I'm on 10.04 indeed, sorry I forgot to mention.

I have a partial back up of the data, however I am surprised I can't get to a shell prompt nor run a LiveCD, it had never happen to me before as a result installing a graphics driver...! I was expecting failure on loading the xserver.

Any hint on how to drop to a shell?

---

### Post by mastablasta on 2011-11-21
are you sure it booted the liveCD? because liveCd boot doesn't have anything to do what you have on hard drive or have installed to hard drive. it doesn't touch the hard drive at all. in fact you could take out the hard drive and boot from CD alone.
 
Also check if the liveCD you have is actually a good one.

---

### Post by QuimNuss on 2011-11-21
Yes, that's what confuses me the most. How is it possible that the LiveCD fails to boot?

I'm wondering that maybe the cd is faulty, since even the Install ubuntu option fails.

I've also noticed that if I don't press a key when the bottom symbol of a keyboard (Accessibility I believe it is) appears the try/install/test/etc. menu does not appear.

I'll give a try to a USB installation or I'll burn another CD and get back to you.

---

### Post by QuimNuss on 2011-11-21
ok that was it, booting from an usb works as usual.

it was indeed the old interface I was dropping to when pressing the keyboard, the other one (with neat graphical interface) failed to boot from cd.

Ok so now the problem would be how to remove the fglrx driver. Since I'm booting from the usb, I can't use the apt-get nor the uninstall script.
What would be the best option to uninstall de driver from a live session?

---

### Post by QuimNuss on 2011-11-21
Ok great, removing the xorg.conf worked. Now I can follow the purge instructions.

[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide)

(and probably back up my data before trying anything else)

---

