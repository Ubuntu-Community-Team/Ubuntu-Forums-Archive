---
title: "Application Location"
date: 2010-04-05
forum: General Help
---

### Post by clydeseal on 2010-04-05
Okay this is like an uber super noob question, but I cannot figure it out and I have been searching the internet for like the last hour trying to find it.

Where are applications located in Ubuntu?

I see the Applications menu, but there is an application, Open Office Formula, installed on the computer, but not present in the menu. On an apple there is a folder named "Applications" and windows has "Program Files" and "Program Data" which stores all of your program information. However I can not find such folder in Ubuntu. Does such a folder exist? If so where is it? If not how can I launch applications that are not found under the applications menu.

BTW I am using Ubuntu 9.10 Karmic Koala.

---

### Post by spiky001 on 2010-04-05
hi this would be installed within open office itself open an office doc i think f2 might control it if not check trhe menu bar format

---

### Post by mickObrian on 2010-04-05
Mine are in /usr/bin.

---

### Post by nothingspecial on 2010-04-05
The linux file system is ordered differently.

Most binary files go in /bin or /usr/bin then there is /lib that contains stuff that many different apps use.

But, to keep this simple, if you install something that does not automatically appear in your menu - try typing the app`s name into a terminal.

But in your case try 

```
ooffice -math
```

---

### Post by clydeseal on 2010-04-05
yup I found it in /usr/bin and was able to launch it that way, but I also tried launching it through terminal and it worked once I spelled it right :oops:

Thanks for your help!
I give you all a smiley star :KS

---

### Post by estyles on 2010-04-05
To make it appear in your menu, go to System->Preferences->Main Menu.  It might already exist under the "Office" tab, but if it's unchecked, it won't show up in the menu.  If it's not there at all, you can click "new item" to add it.

---

### Post by dnairb on 2010-04-05
Right-click "Applications" in the panel and select "Edit Menus"

Click "Office" in the left-hand pane, and you will see "OpenOffice.org formula"  in italics in the right hand pane.

Click it, so it has a check mark, close the window and you should then have access to formula via Applications --> Office

---

