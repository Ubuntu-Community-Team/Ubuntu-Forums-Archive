---
title: "no sound in Ubuntu 10.04?"
date: 2010-09-15
forum: General Help
---

### Post by MachoMan1350 on 2010-09-15
Hello, i am new to Linux and i just installed Ubuntu 10.04 and have run into a problem - theres no sound. i have opened the system preferences and the alsamixer thing and set everything to its highest setting, but still no sound. any suggestions?

I'm running ubuntu off of a 64-bit laptop if this helps.
thanks in advance

---

### Post by zaphod777 on 2010-09-15
what kind of computer do you have?

---

### Post by FahadMKS on 2010-09-15
If you use a Sound Card in the computer, you may select System >> Administration >> Hardware Drivers and check if you have a driver to get installed.

If it is there, Install it and then restart the computer and then check if the issue is solved.

You may also check for the if the System Sound option on the top taskbar is set to correct level.

---

### Post by MachoMan1350 on 2010-09-15
I'm pretty sure its an HP G72t series
320gb hardrive, 4gb ram, 64bit

---

### Post by zaphod777 on 2010-09-15
hmmm you might try posting in this thread as these guys have the same machine.
[http://ubuntuforums.org/showthread.php?t=1441816](http://ubuntuforums.org/showthread.php?t=1441816)

but acording to them it should work. One person had to re-install to get the sound working. I would Suggest making sure it is fully up to date also.

Before you go re-installing I would try uninstalling Alsa and re-installing alsa and restarting to see if it works.

Run these commands from the command prompt.
```

sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils 
sudo apt-get install linux-sound-base alsa-base alsa-utils 
sudo apt-get install gdm ubuntu-desktop
```

---

### Post by zaphod777 on 2010-09-15
Also I would check and make sure there are no hardware switches that are muting the sound.

---

### Post by FahadMKS on 2010-09-15
Please post the output of these terminal commands for me please:
Terminal="Applications->Accessories->Terminal"
Please post text output using code tags. Also helpful is the make/model of your PC/Laptop.
```

```
uname -a aplay -l cat /proc/asound/version head -n 1 /proc/asound/card*/codec#*

---

### Post by cogier on 2010-09-15
zaphod777 makes a valid point, don't dismiss it. Check that the sound is not muted. It has caught me out before.

---

### Post by zaphod777 on 2010-09-15
> **cogier said:**
> zaphod777 makes a valid point, don't dismiss it. Check that the sound is not muted. It has caught me out before.

Me too I was going crazy one time until I found that the button on the laptop was a hardware mute and no matter how much I played with the sound settings it wouldn't effect the button. I sure gave myself a face palm after I found it.

---

### Post by MachoMan1350 on 2010-09-15
I've checked for hardware interference, but everything is normal. A few days ago i booted Ubuntu off of a usb (i was using windows at the time) and there was no sound then either, but when i went back into windows and there was sound. so then i was thinking it had to be Ubuntu, not my laptop....

@FahadMKS i entered the code but it said "uname: invalid option -- 'l'
Try `uname --help' for more information."

maybe i entered the code wrong?

---

