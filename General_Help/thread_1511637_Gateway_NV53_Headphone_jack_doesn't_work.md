---
title: "Gateway NV53 Headphone jack doesn't work"
date: 2010-06-17
forum: General Help
---

### Post by requeth on 2010-06-17
I'm on a Gateway NV53 with a CX20571 Hermosa HDA ATI SB intigrated sound card. My speakers work fine, but when I plug into the headphone jack nothing happens. The speakers keep playing, and the headphones don't pick up anything other then a "click" like you would expect when jacking in if no sound was being played. I checked alsamixer and all devices except the headphone output are being displayed.

Anyone know how to fix this problem? I havn't been able to find anything useful searching the web.

Thanks in advance.

---

### Post by lidex on 2010-06-17
Try this. Using a Terminal="Applications->Accessories->Terminal"
Open this file for editing:
```
 gksudo gedit /etc/modprobe.d/alsa-base.conf 
```
Insert these lines at the bottom:
```
options snd-hda-intel model=laptop
options snd-hda-intel position_fix=1 enable=yes 
```
Save. Close. Reboot. Check your levels in alsamixer.
```
 alsamixer 
```
Press <F6> to select the correct soundcard.
Press <F3> to show playback levels. <F4> selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. <M> to mute/unmute.
Go to "System ->Preferences ->Sound" and make sure the correct soundcard is default and adjust your profile on the hardware tab.

---

### Post by lazyrobot47 on 2010-06-28
Fix worked great man, I was having the same problems! I have a Gateway NV53 as well. Now only if i could get my internal webcam issue solved...

---

### Post by Kaldim on 2012-01-11
I wanted to note that this fix worked on my Macbook 2.1. (ubuntu 10.10). As of January 11, 2012.

Thank you guys for this wonderful forum!

---

