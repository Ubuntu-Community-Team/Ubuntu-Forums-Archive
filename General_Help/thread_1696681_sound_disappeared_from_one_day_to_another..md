---
title: "sound disappeared from one day to another."
date: 2011-02-27
forum: General Help
---

### Post by jakupl on 2011-02-27
I use an ubuntu computer as a media center, and suddenly today when I turned it on, there was no sound. I think that I have checked for all the obvious stuff. Changed loudspeakers, checked the mute button and volume. I don't think that I have changed anything. What could this be except hardware failure? "I use the built in sound from the motherboard"

Any help is greatly appreciated

---

### Post by jakupl on 2011-02-28
I tried booting the live cd, and the problem persisted. There was still no sound, but if I disconnect the keyboard, I actually hear a voice saying "no keyboard detected" when I reach bios.

So I tried inserting a second sound card, Ubuntu identifies it correctly but still no sound :(

Any ideas anyone? Any help is greatly appreciated.

---

### Post by celldweller1591 on 2011-02-28
(1)

---

### Post by celldweller1591 on 2011-02-28
Sometimes, sound might be configured correctly, but for some reason or another (tinkering) it stops working. One way to go back to the old setup is to reinstall Ubuntu. However, this step is actually quite unnecessary since you are reinstalling everything because of one thing.

A faster way, is to just remove the problematic packages and reinstall them cleanly. 

(1) Remove these packages
> sudo apt-get --purge remove linux-sound-base alsa-base alsa-utils

(2) Reinstall those same packages
> sudo apt-get install linux-sound-base alsa-base alsa-utils

IMPORTANT NOTE: Ubuntu (GNOME) users have reported that packages 'gdm' and 'ubuntu-desktop' are removed after removing the linux-sound-base packages. If this happens, then do the following
> sudo apt-get install gdm ubuntu-desktop

(3) Reboot

Now you may ask "I already had the packages, so why did I go through the trouble of removing them, then installing them". The answer lies in the --purge option which removes all the extra information that accumulated from tinkering and upgrading. After doing a purge then install, the packages are unpackaged as if it they are brand new.
(4) At this point, try using
 > aplay -l
you should get your soundcard listed.

---

### Post by jakupl on 2011-02-28
Thanks for the help.

However, the sound did not come back from reinstalling those packages, here is the output of aplay -l


```
jakup@boxeetelda:~$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

---

### Post by jakupl on 2011-02-28
And again, I have the same problem when I boot the live cd. And changing soundcards does not work.

---

### Post by jakupl on 2011-03-01
bump

---

### Post by searchfgold6789 on 2011-03-01
Here is a great guide that may help you:
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

---

