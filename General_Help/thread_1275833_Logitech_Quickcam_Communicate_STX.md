---
title: "Logitech Quickcam Communicate STX"
date: 2009-09-26
forum: General Help
---

### Post by TarasIv on 2009-09-26
How do I configure this webcam to work with Skype? Thanks!

---

### Post by TarasIv on 2009-09-26
*bump*

---

### Post by smartsmokey on 2009-09-26
hmmm this is going to be quite a project. It will work with skype, but you will lose a lot of time and sanity. I'm pretty ripped right now so I can't find much, but just try searching for quickcam and skype...the former is more important right now. BAsically it's a huge pain in the ***. But once you get it, it's okay.

---

### Post by howefield on 2009-09-26
Try typing lsusb into a terminal to find the "ID" associated with your webcam, then use your favourite web search engine for that ID and Ubuntu.

Maybe something will turn up.

---

### Post by TarasIv on 2009-09-26
Will try and will post how it goes.

---

### Post by Zill on 2009-09-26
According to [this site]("https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech"), it used to work with the older versions of Ubuntu but no longer does. :-(

However, it may be worth trying the fixes listed in [this bug report]("https://bugs.launchpad.net/ubuntu/+source/gspca/+bug/291723") (#291723).

If that fails I suggest you get a more recent webcam that uses the uvcvideo driver.

---

### Post by TarasIv on 2009-09-27
Ok, I've got it working, but I have to launch Skype using this command every time in terminal:
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
Anyway to shortcut this? Also, is there anyway for it to automatically adjust light, this is a minor issue, but any help is still appreciated. Thanks a lot Zill!!!!

---

### Post by Zill on 2009-09-27
TarasIv:  If you have a Skype entry in your menu, you should be able to edit the properties so that your wrapper replaces the old Skype command:

Right-click on the main "Applications" menu and select "Edit Menus" to open the Alacarte Menu Editor.

Select the appropriate group containing the Skype menu entry.

Right-click on "Skype" and select Properties.

In the Entry Editor, make a note of the old Command (probably just Skype but it is always wise to make sure!).  Replace this command with the full command wrapper you posted above (preferably by pasting to eliminate any typos!).

Close the Entry Editor and the Alacarte Menu Editor.  That's it!

Caveat:  I used the Ubuntu 6.06 menu editor for this so it may have changed *slightly* in later versions. :-|

---

### Post by TarasIv on 2009-09-27
Zill: It won't work the way you said. I get the error that it cannot execute the child process and no such file or directory exists. Any other way you recommend?

---

### Post by TarasIv on 2009-09-27
*bump*

---

### Post by TarasIv on 2009-09-27
*bump*

---

