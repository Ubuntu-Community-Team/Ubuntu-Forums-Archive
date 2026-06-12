---
title: "Monitor Shuts Off before Login Screen. Not on XP"
date: 2010-07-22
forum: General Help
---

### Post by Cosmic Charlie on 2010-07-22
Howdy all,

When I boot up my computer, the monitor turns on, and allows me to do what I want in the BIOS, and grub boot menu, but right before I get to the Ubuntu (10.04) login screen, the monitor shuts off.

Interestingly, this started to happen AFTER my house got hit lightning (i do have a belkin surge protector)!! It could be a coincidence I think, because the monitor seems to work until the Ubuntu login screen. This DOES NOT HAPPEN WITH WINDOWS XP! The monitor works all the way through on XP boot up. I've also tried a different monitor.

I've tried hitting [CTRL]+[Alt]+[+or-] which is supposed to change the video card mode, but it does nothing. Booting into terminal via grub menu works fine.

My video card is a Nvidia 6800 GT. And I have the NVidia drivers installed on the machine..

Any Suggestions? Can anyone tell me how to uninstall the nvidia drivers via terminal? I think this will solve my problem.

Thanks
-Gabe

---

### Post by Cosmic Charlie on 2010-07-22
Progress!

So after a bit of research (more time than it should have taken), i found the command:
```
sudo apt-get --purge remove nvidia-*
```
to remove the nvidia driver. That command will remove ALL nvidia drivers.

After typing that in i did a ```
sudo reboot
```

PC rebooted, graphics said it couldnt find NVidia drivers because the module didnt exist.
I set the default graphics config, now im back to my desktop. sooo, success!!

The weirdest thing is that after my house having been hit by lightning, and having this weird nvdia driver problem after hahaha, now my ethernet port on my PC isn't working. What in the hell. Anyway, this thread is solved. Thanks (for nothing)!

---

