---
title: "Deleting and Reinstalling Firefox..."
date: 2010-10-22
forum: General Help
---

### Post by wbee on 2010-10-22
Hello,

I was on line and viewed a Picassa slide show. I went to F11 for the full screen and after I closed Picassa,my Firefox browser had been reset,creating all kinds of issues,taking out my status bar,making it impossible to access the three icons in the top right hand corner of the screen,and so forth.

When I removed and reinstalled Firefox from the Synaptic Package Manager,it did not give me the option of not saving the settings and the same issues pertained to the newly installed one.

Does anybody know the shell code to remove and reinstall the Firefox Browser unsullied,pristine,not saving the existing settings?(realizing I'll lose the bookmarks and have to set it up anew?)

--------------

Thank you.

---

### Post by ivarn on 2010-10-22
Close firefox, go to your home folder > .mozilla, there you'll see the firefox settings and history folder, delete it and restart firefox.

---

### Post by wbee on 2010-10-22
Ivarn,

I tried that and got to some Mozilla folders,but could not find any labeled Firefox settings and history.

??

(Thanks though:-)

---

### Post by wbee on 2010-10-22
Here is what I have so far:

(My home name>.mozilla>firefox>8x61m5vO.default and crash reports and profiles.ini. Within those three areas,I could not find settings and history.

---

### Post by WorMzy on 2010-10-22
Deleting the firefox folder will force Firefox to create a new profile, using all the default settings (this includes bookmarks). If you're looking for a place to edit your settings, open firefox and then go to Edit -> Preferences, and direct your browser to [about:config]("about:config").

To delete history, go Tools -> Clear Recent History.

---

