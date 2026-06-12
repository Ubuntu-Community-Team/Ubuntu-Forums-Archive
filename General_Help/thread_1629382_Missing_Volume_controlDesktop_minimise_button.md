---
title: "Missing Volume control/Desktop minimise button"
date: 2010-11-23
forum: General Help
---

### Post by mixtri on 2010-11-23
Hello guys.
I have recently had my ubuntu  10.04 updated and lost the show desktop (minimise button usually attached to the desktop panel located at the bottom far left corner of the screen. (The one you click on which minimises all windows and takes you direct to the desktop.
Can anyone help with getting it back?
I have tried looking for options in the Appearance and Windows options in Menu-system-preferences but cant find anything, that could be used to enable or disable this feature.
Secondly, since upgrading to the current version of Ubuntu I have been missing the volume control button usually located  by the date/wireless/ Power off button/ icons on the panel located top right of screen.
Any suggestions would be much appreciated.
Thanks

---

### Post by tony.mcconnell on 2010-11-24
Hi I cant help you with the first problem, but I can help you with the second one.

If you right click the panel -> Add to Panel --> Indicator Applet you will get your volume control back. The problem with this is that theres also a mail icon added which cannot be got rid of individually. To get around this I removed the Indicator Applet from the panel by right clicking and selecting "remove from panel".

Then:

1) System -> Preferences -> Start Applications

2) Add the Volume Control the name is "Volume Control" and the  command is "gnome-volume-control-applet"

3) restart, then you will have a single volume control (come to think of it you may not even need to restart.

---

### Post by tony.mcconnell on 2010-11-24
Whoops I meant 1) System -> Preferences -> Startup Applications

---

### Post by nl4m on 2010-11-24
To get back the "Show Desktop" icon right click the panel and click on "Add to panel" and choose "Show Desktop" or as a shortcut you can use "CTRL"+"ALT"+"D".

---

### Post by mixtri on 2010-11-24
Thanks guys, I got the show desktop back.
As for the volume, Tony, volume control does not appear in startup application preference box. I suppose I need to add it from somewhere else. Any ideas where that could be?
I really do like ubuntu for lots of reasons, but there are times when simple stuff like replacing a volume control which imo should be straightforward and easy enough to locate becomes a frustrating experience.  
Common sense dictates anything to do with volume control would be located under SYSTEM/PREFERENCE/SOUND, or have a context of its own. 
Why its been located under SYSTEM/PREFERENCE/startup applications is totally beyond me 
And why is it I always have to replace missing applications or certain system functions after updating the system? Very frustrating indeed?
I guess i shall pass my feedback onto the ubuntu tech guys.
Thats my rant over:p
Thank you guys, much appreciated.
Albert

---

### Post by tony.mcconnell on 2010-11-24
Hi Mixtri,

Yes you are right  the volume control does not appear in startup application preference box, so you need to add it to there. To to this go into System -> Preferences -> Startup Applications and then select the "Add" button. In the dialog box that appears you will have to put in a name and a command,

The name is  "Volume Control" and the  command is "gnome-volume-control-applet", then hit "Add". After you have done this you should see "Volume Control" as one of the startup applications in the list.

Then you should be ok, you might have to do a restart, I dont remember. Good Luck!

---

### Post by mixtri on 2010-11-24
Tony, you are the best!
Got my system back to the way I want it. Thanks a lot!

---

### Post by tony.mcconnell on 2010-11-24
You are welcome! It takes a bit of time to get used to Linux, but this is a great forum and many people will have experienced the same problems as you. So generally you'll get an answer. Cheers.

---

