---
title: "Rhythmbox requires 2 clicks to start."
date: 2010-08-08
forum: General Help
---

### Post by fterh on 2010-08-08
First time I click on the launcher on the panel, the process starts. I have to click on it again to open up the GUI of the application. Normal? :(

---

### Post by ed-koala on 2010-08-08
I have the same issue.  Rhythmbox is starting minimized to the panel.  I'd like to make it start on screen also.  How can that be changed?  There is no option from within Rhythmbox.

---

### Post by fterh on 2010-08-08
> **ed-koala said:**
> I have the same issue.  Rhythmbox is starting minimized to the panel.  I'd like to make it start on screen also.  How can that be changed?  There is no option from within Rhythmbox.
And when I exit Rhythmbox the music still plays unless I end process.

---

### Post by ed-koala on 2010-08-08
What's happening is you are not actually ending Rhythmbox if you click the X button.  It just goes back to tray and keeps playing.  To fully exit you must choose "exit" from the file menu.

Still want to change the startup minimized though.

---

### Post by arrimapirate on 2010-08-08
A simple way to get Rhythmbox to open with a gui as soon as you click it is to right click the shortcut and click properties. Under "Command:" where it says "rhythmbox" change it to rhythmbox-client.

Unfortunately this only works on shortcuts and not the menu entry.

---

### Post by fterh on 2010-08-09
> **arrimapirate said:**
> A simple way to get Rhythmbox to open with a gui as soon as you click it is to right click the shortcut and click properties. Under "Command:" where it says "rhythmbox" change it to rhythmbox-client.

Unfortunately this only works on shortcuts and not the menu entry.
Thanks. A question though: how do you go about finding workarounds like these? Are they listed under rhythmbox's official manual or what?

---

### Post by stinkeye on 2010-08-09
> **fterh said:**
> First time I click on the launcher on the panel, the process starts. I have to click on it again to open up the GUI of the application. Normal? :(

rhythmbox > edit > plugins 
Enable the Status Icon plugin
Click on configure and set the status icon to always visible.

---

### Post by fterh on 2010-08-09
> **fterh said:**
> Thanks. A question though: how do you go about finding workarounds like these? Are they listed under rhythmbox's official manual or what?
bump my question up :D

---

### Post by WorMzy on 2010-08-09
> **fterh said:**
> Thanks. A question though: how do you go about finding workarounds like these? Are they listed under rhythmbox's official manual or what? 

Yes, reading man pages often tips you off to "hidden" features like this.

> A simple way to get Rhythmbox to open with a gui as soon as you click it is to right click the shortcut and click properties. Under "Command:" where it says "rhythmbox" change it to rhythmbox-client.

Unfortunately this only works on shortcuts and not the menu entry. 

You can edit the menu items by running alacarte.

---

### Post by arrimapirate on 2010-08-09
> **fterh said:**
> Thanks. A question though: how do you go about finding workarounds like these? Are they listed under rhythmbox's official manual or what?

Actually i was just poking around the /usr/bin directory and found the rhythmbox-client file.

---

