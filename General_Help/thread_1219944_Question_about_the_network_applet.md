---
title: "Question about the network applet"
date: 2009-07-22
forum: General Help
---

### Post by 0re0 on 2009-07-22
I want to do some customizing of the icon for my wireless network status. I have changed other icons for things but am a little lost on this one. 
Im using the mac4lin set of icons and when i got to .icons/mac4linicons/ there is a list of different sized icons andwithin each set of sizes there is an apps folder that has gnome-network status icons and nm-network-status icons. So I do not know which size and which set of icons the panel network status reads off

---

### Post by Vadi on 2009-07-22
Standard size of the panel dictates 16x16, I think. If you increase the size of the panel, it'll use the next available one.

---

### Post by 0re0 on 2009-07-22
replaced icons in there and so no change, i guess a beter question is rather then changing the icons notification area uses is can i change where the applet looks,through gconf-editor or gedit?

---

### Post by 0re0 on 2009-07-22
i solved this, incase anyone else was thinking this. i had to change the nm-network-status in the scalable folder, This is my guess but i believe the manager looks in scalable for a work able png and if it does not find one then it will look under the size specific folders

---

