---
title: "Disable S/PDIF"
date: 2010-04-27
forum: General Help
---

### Post by lvalen18 on 2010-04-27
On Windows 7 S/PDIF (digital Audio) is disabled by default.. When enabled i get this statics/ white noise on my left speaker... So i leave it disabled and im happy with the playback sound... ON Ubuntu this same sound is aways on... I figured thats Ubuntu has this enabled im guessing by Pulse... So is there away to disable this feature that my speakers dont like?

---

### Post by lidex on 2010-04-27
Try using alsamixer in a terminal. Terminal="Applications->Accessories->Terminal":
```
 alsamixer 
```
Press F6 to select the correct soundcard.
Press F3 to show playback levels. F4 selects capture levels [or use <Tab>]
Use the left/right arrow keys to select and up/down arrow keys to change levels. Scroll to the correct element and press 'm' to mute.

---

### Post by CLEARviewF on 2010-04-27
Well,

As I already did. You can disable the digital output from the main menu in: /Preferences/Sound/ and go to the Hardware tab and disable what you want by selecting the right device and then choose "Off" in the roll-down menu.

Regards!

---

