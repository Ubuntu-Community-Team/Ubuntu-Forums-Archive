---
title: "Black screen with cursor after hibernate"
date: 2009-11-27
forum: General Help
---

### Post by LordIshamael on 2009-11-27
Hey, I'm using a Dell XPS 13 running Kubuntu 64 bit. I just hibernated my computer, and upon resuming, it enters grub perfectly. I then have the option of either Kubuntu or Windows. There are 2 kernel versions of Linux, and a recovery mode option for each one - four in total. Booting into any of them leads me to a black screen with a cursor. The cursor initially moves down two lines, then a slight flash of the old image (kubuntu loading before the login screen) comes, although horribly distorted, and thenthe cursor reappears on the black screen at the top, and continues blinking furiously. I have left it for a long time, but nothing happens from there.

I did just install the ubuntu-studio package before hibernating. I had also used usplash to set the 'text during boot' option to off. I had also selected a custom image as bootsplash. However, the changes to usplash were made before, and I had restarted after those with no problem.

It clearly isn't a problem with grub, since the option to boot into Windows works just fine.

I can't even access the recovery mode or console or type anything, just a blank screen.

Thanks for any help!

---

### Post by audiomick on 2009-11-27
Hallo. I have read frequently that the swap partition needs to be bigger than the RAM in order for suspend and hibernate to work. Is this the case on your machine? Did the hibernate work before you put Ubuntu studio on?

Neither suspend nor hibernate work on mine, but I haven't bothered to try and find out why. If I go away from the computer for any length of time, I just turn it off. 

I am using Ubuntu Studio 64 bit.

---

### Post by LordIshamael on 2009-11-27
No, I have never tried hibernating before this. I have, however, suspended successfully on occasion. No, my swap is not larger than my RAM (considering I have 4 gb RAM, it seemed like a waste).

Edit: Actually, the hibernate was a bit of a mistake, my mouse slipped - I was going for restart. I do not plan to hibernate again, however since I have suspended successfully before, I do plan to again, and I don't think there should be any problems...

My main concern right now is getting my laptop back online. Isn't there a way to make it ignore the hibernate option and go straight into normal booting, if that is where it is stuck, but then why would there be a problem with the recovery mode too?

---

### Post by LordIshamael on 2009-11-27
OK, following something posted elsewhere, I edited the boot command, adding acpi=oldboot to it. This had no effect. However, while there, I noticed some commands pertaining to the splash. I removed them and ran that command. This gave me a couple of errors, and then opened my desktop.

I do not mean the login screen, I mean that it displayed my screensaver, with the widgets, and said that the screen had been locked - as though it had been locked all along. When I logged in, the programs I had when I hibernated were still open as well.

Not sure if this will survive a reboot, but as long as I do not hibernate again, it hopefully will not be a problem...

Oh, and I have around 2 GB of swap, but suspend works fine, contrary to what some others say.

Suspend saves to RAM, while hibernate saves to swap. Perhaps that makes the difference...

---

### Post by LordIshamael on 2009-11-30
It was probably a defective splashscreen, as after changing my bootsplash, my computer is back to normal.

---

