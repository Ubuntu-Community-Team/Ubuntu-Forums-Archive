---
title: "How to add a new icon"
date: 2010-03-04
forum: General Help
---

### Post by inearlygaveup on 2010-03-04
Can anyone tell me how to add a new icon to the systems "Menu Icons" I can't find where they are stored !
( I have installed Google Chrome and have added a Launcher to the panel but I have no icon for chrome to allocate to it)

Martin

---

### Post by gsmanners on 2010-03-04
You should put icons into /usr/share/pixmaps and select "Image Files" from the mode selection in the file dialog.

---

### Post by devwillie on 2010-03-18
I'm using xubuntu 8.04 but cannot add the launcher for Chrome b/c I don't know where it's installed.

Right-clicking on the Chrome icon in the panel menu just opens Chrome.  There's no option to send a launcher to the desktop.

And I don't want to upgrade to 9 b/c the laptop is ancient.  I used to run 9.04 and noticed a BIG difference in performance between 8 and 9. xUbuntu seems to be getting heavier all the time.

Any ideas about Chrome?

-dw

---

### Post by inearlygaveup on 2010-03-18
I am not an expert but I did this
Right click on a panel - pick Add to Panel – click on Custom Application Launcher (On mine it was the first)
Pick – Type Application 
Name it Google Chrome
Command (find chrome) mine was in  /opt/google/chrome/google-chrome %U
Comment type Access the Internet

Click on ok – it should now work but it may not have picked up the Google Icon, if not I found mine in  /usr/local/share/icons/hicolor/48x48/apps/google-chrome.png

Hope it works for you, as I said I am not an expert like lots of the guys on hear, you may get a better set of instructions from someone else

---

### Post by devwillie on 2010-03-19
Martin,
Everything worked.  Thanks!
How did you find the locations of the chrome app and icon file?

I didn't have much luck in google and wasn't patient enough to use 'find' on chrome* items.

That's great!  Such a great response from over the pond.

dw

---

### Post by inearlygaveup on 2010-03-19
Glad it worked for you.
I found the Chrome app by just clicking on the open folder icon on the right hand side of the command line and looked for Google Chrome (after I couldn't find it under chrome).
I found the Chrome Icon by doing a file search.

---

### Post by bobcollard on 2010-03-19
> **inearlygaveup said:**
> Can anyone tell me how to add a new icon to the systems "Menu Icons" I can't find where they are stored !
( I have installed Google Chrome and have added a Launcher to the panel but I have no icon for chrome to allocate to it)

Martin
/usr/share/icons

---

