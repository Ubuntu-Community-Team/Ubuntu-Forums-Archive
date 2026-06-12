---
title: "HDMI audio not working"
date: 2010-12-27
forum: General Help
---

### Post by getburned2098 on 2010-12-27
I have ZOTAC ZBOXHD-ID40-U with the newest version of ubuntu installed
 hdmi audio is not working but the analog audio is working. 
I look in the alsamixer all settings are unmuted. 
Need help I'm a noob :(

---

### Post by efflandt on 2010-12-27
What does **aplay -l** (small L) show for audio devices.

If you unmuted the S/PDIF devices in HDA NVidia of alsamixer, sometimes it is just a matter of finding out which one works with:

```
aplay -D plughw:**card#**,**device#** /usr/share/sounds/alsa/Front_Center.wav
```Where card# is card number (often 0 or 1), and try each device# (often 3, 7, 8, 9) until you hear it.

For my GT 430 it was plughw:1,9 so I added the following to /etc/pulse/default.pa after the alsa-sink line (you have to do that as root, so use **gksu gedit /etc/pulse/default.pa**)
```
#load-module module-alsa-sink
**load-module module-alsa-sink device=hw:1,9**
```Reboot and see if you can switch Outputs in Sound Preferences while playing something in Rythmbox or your favorite audio player.  However HDMI might be a different one than you expect (for me HDMI works for the HDA NVidia that does NOT say HDMI).

---

### Post by getburned2098 on 2010-12-28
Thanks, that helped and some other stuff i found from googling :)

---

### Post by Petomni on 2011-02-01
> **getburned2098 said:**
> Thanks, that helped and some other stuff i found from googling :)

Could you detail how you got your ID40's audio working? I'm running 10.10 and going through all the forums about fixing this but can't seem to find any tips that work specifically for this box. I am in the same spot as you were, I can get analog sound to work through the 3.5 jack but not through HDMI.

Cycling through all the cards/devices with aplay results in no sound for any combination except the analog 0,0 (as I said above).

plz plz help!

---

