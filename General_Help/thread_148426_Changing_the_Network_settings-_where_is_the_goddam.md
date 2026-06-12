---
title: "Changing the Network settings- where is the goddamn button???"
date: 2006-03-22
forum: General Help
---

### Post by SunshineSmile on 2006-03-22
Hi folks! Writing this from my roommate's windows comp. I have moved, and I need to change the network settings. In my old appartment, I had to manually enter the IP address upon installation. Now I need to undo this, *but I can't figure out how!!*

Under network settings, it says I have to enter administrator mode to change the settings, **but the button for administrator mode is no way to be found in the window**, and the bloody window won't show its lower edge, even when I pull the taskbar away. Arrghh..

---

### Post by Jucato on 2006-03-22
Have you tried resizing+moving the network settings window?
Anyway, here's a workaround for that: use KControl instead of System Settings:
1. in a Run Command dialog box (Alt+F2), type in kcontrol
2. Look for Network Settings under Internet and Network
3. You will have scroll bar that will let you scroll down to the Administrator Mode button.

---

### Post by SunshineSmile on 2006-03-22
Yeah, I had tried resizing, to no avail. Kcontrol provided the "administrator mode button" Thank you.

However, klicking the admin button and typing in my password, didn't allow me to change anything-- I was just shipped back to the kcontrol mainscreen.. Sux.

Seeing as it automatically searches for my connection, could it be that the reason I can't change my settings is that I aint't connected? I.e, my computer won't recognize my new D-Link USB 2.0 Adapter..

---

### Post by MJN on 2006-03-22
With regards to the admin button I know where you're coming from - whoever designed the HCI (or lack thereof) for those windows needs shooting.
 
**ALT-M** is your friend there (keyboard shortcut).
 
Mathew

---

### Post by sleepkreep on 2006-03-22
Alternatively, you can start kcontrol with root permissions.  Hit <Alt>+<F2> and type *kdesu kcontrol*.  Type in your password and kcontrol will start with root permissions.  This way you won't have to worry about the administrator button.

---

