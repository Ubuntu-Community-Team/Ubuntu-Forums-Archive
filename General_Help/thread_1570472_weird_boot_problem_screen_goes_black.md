---
title: "weird boot problem screen goes black"
date: 2010-09-08
forum: General Help
---

### Post by ravengirl1960 on 2010-09-08
I'm going through this again. I posted this here as well as in the Mint forums because the architecture is very similar. What happens is that when I reboot, the screen goes black at the steps of the boot after about three seconds with each step. So I see the bios enumeration, then the screen goes black; I see the start up sequence with "Linux Mint" and the green/white dots beneath it, then the screen goes black; then finally, I hear (but don't see) the beep when the password login prompt shows.

But if I get into the bios (dealing with the screen going black each time) and change it to "load default settings", then it reboots and works fine. Till the next time I boot.

---

### Post by Rubi1200 on 2010-09-09
Hi,
can you please tell us what graphics card you have installed?

Thanks.

---

### Post by ravengirl1960 on 2010-09-09
Oh, I'm sorry, I'm an idiot. :P

nVidia GeForce 6600.

This problem happens in both Ubuntu flavors I've used (Ubuntu 10.04 LTS and Linux Mint Helena).

It's aggravated by what I thought was the scrrensaver properties but not so sure now. If I leave the puter on for more than 20 minutes or so, it goes black again. When I move the mouse, the display shows for a second, then goes black again. If I leave it on but not using it for a long time, it goes black and 'locks' and I have to reboot.

I've shut off the power management 'sleep' functions, I've shut off (as far as I can tell) the screensaver activation and yet this still happens. And then, of course, when I reboot, it starts all over again.

This happened with my previous install. So (for other reasons as well) I bought a brand new terrabyte drive and did a clean install. And it's still happening.

---

### Post by Vigh on 2010-09-09
if possible in bios set powermode settings to S1, it usually more stable, have you tried installing the official drivers for your graphics card? this may solve your problem

---

### Post by Rubi1200 on 2010-09-09
When you boot the computer and the GRUB menu comes up highlight the entry and hit "e" to edit.

Find the line that ends with ```
ro quiet splash
```Remove quiet splash and replace with nomodeset then "Ctrl" + "x" to boot.

See if that resolves anything and report errors or problems back here.

Also, under System > Preferences > Screensaver did you also untick "Activate screensaver when computer is idle" and "Lock screen when screensaver is active"?

Finally, do you have desktop effects (Compiz) turned on? Try turning it off and see if that makes any difference.

Hope this helps.

---

### Post by ravengirl1960 on 2010-09-14
Okay, I changed the grub. I'm going to reboot and see if that changes anything (I may have to reboot several times; the "work/doesn't-work" factor is random).

As to the screensaver properties, yes. I've tried that in both Gnome and KDE to no avail.

And also, I have an onboard ATI 3300 video chip that I'm currently running on and it's doing the same thing, shutting off the display every 2-3 seconds.

One note: I have a SOYO flatscreen monitor. When this stuff happens, I can push a button to switch it from RGB to DVI. It doesn't last but when it switches back to RGB, the display comes back on for about 2 seconds.

---

### Post by lidex on 2010-09-25
Perhaps a BIOS/ACPI issue??
What do you get for this:
```
sudo dmidecode -t bios
sudo dmidecode -t baseboard

```
Also scan your dmesg for any clues.

---

