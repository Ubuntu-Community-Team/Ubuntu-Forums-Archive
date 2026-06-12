---
title: "Sorry - confused about 12.04 system tray"
date: 2012-06-04
forum: General Help
---

### Post by Quarkrad on 2012-06-04
I'm running 12.04 Unity on my 64bit machine. I have got Skype working with video (having had to edit the .desktop file) but when you close Skype down the app is still running.  In gnome 2 days there was an icon in the top panel that you had to right click in order to either log out or close down Skype.  At the moment, on the Unity Desktop, I have to launch System Monitor in order to kill the Skype process.  There are some articles on getting the Skype icon in the System Tray in 11.04 and 12.04 but what/where is the System Tray? Is it the top panel?   I am forcing myself to use the Unity desktop but stuggling to locate this System Tray.  There must be an easier way to cleanly close down Skype other than having to go via the System Monitor app.

---

### Post by zombifier25 on 2012-06-04
The system tray is like that of in GNOME 2 - top right corner, where you see your notifications and stuffs. Skype does not support Unity's system tray by default yet, so follow the tutorials you found to add it.

---

### Post by inashdeen on 2012-06-04
I am not sure what is the bug you are  having, but my skype minimize perfectly to the system tray. all i need to do is to right click icon on system tray and press quit to kill skype.

---

### Post by 3rdalbum on 2012-06-04
Skype should appear in the notification area. (note: That area is officially known as the "notification area" in Windows and Linux. It is NOT the "system tray", especially not on Linux).

If it doesn't appear in the notification area which is the area you expect it to appear in, then you may have altered your whitelist settings. Ubuntu has depreciated the notification area API in favour of the Indicator API, but keeps Skype in a "whitelist" to allow its icon to appear. If you do a Google search for "indicator whitelist" you should be able to find some instructions for how to alter the whitelist or set it to "all".

But yes, by default Skype's icon should definitely appear in the notification area on the top panel, whenever Skype is open. It does on my machine.

---

### Post by inashdeen on 2012-06-04
agree with 3rdalbum

---

### Post by Quarkrad on 2012-06-04
Thank you for your replies.  I deleted Skype via Synatic and reinstalled through the software center.  It all works now including icon in top panel.   Many thanks.

---

### Post by inashdeen on 2012-06-04
Congratulations :) don't forget to mark as solved

---

