---
title: "Chromium wont become default browser"
date: 2011-05-09
forum: General Help
---

### Post by jesse.au on 2011-05-09
I installed chromium through the software center but every time I open it up it reminds me that it is not the default browser. I click "make default" every time but my computer still makes firefox the default browser. How do I change this??

---

### Post by edm1 on 2011-05-09
Changing the setting in System Settings>Preferred Applications may work.

---

### Post by satanselbow on 2011-05-09
If you have both firefox and Chromium to "check whether X is default" you will keep yo-yo-ing between the 2 and the ubuntu "set default app" will not be able to override either as far as I can tell.

Make sure the tick boxes are not filled as you will go round in circles forever. ;)

---

### Post by MolsterS013 on 2011-05-09
There are two options:

One, you can uninstall Firefox through the Ubuntu Software Center. This should force Ubuntu to set Chromium as your default browser.

Two, you can go to the "System" drop down menu in the upper left corner of your desktop. Here, choose Preferences, then choose Preferred Applications. Choose the "Internet" tab and choose Chromium for your default browser. If it doesn't work right away, try rebooting.

There might be a way to do it via command-line, but I'm not very good with that yet. Hope I helped.

---

### Post by Yasawas on 2011-05-09
> **MolsterS013 said:**
> 
 
Two, you can go to the "System" drop down menu in the upper left corner of your desktop. Here, choose Preferences, then choose Preferred Applications. Choose the "Internet" tab and choose Chromium for your default browser. If it doesn't work right away, try rebooting.
 
 
I've installed Natty twice in the last week and this has not worked on its own. 
 
However, if you do the above, leave that window open, then open Chromium and select "Set as default" again it should remember your preference this time. A little inelegant, but worked for me both times.

---

### Post by jesse.au on 2011-05-09
Works fine for me now. Thanks!

---

### Post by janpieterz on 2011-05-09
Well, I have the same problem, the only difference is no fix helps. Every time I start Chromium it gives the message that it isn't my default browser, though if I look in the system settings it is. Besides that it's the only installed browser (Firefox removed). 

Any Ideas? Also tried Yasawas's fix.

---

### Post by pcastell on 2011-05-13
Make sure ~/.local/share/applications/mimeapps.list exist.
If the file is not there chromium will fail to set it self as default browser.

```

mkdir -p ~/.local/share/applications
touch ~/.local/share/applications/mimeapps.list

```

---

### Post by jobsonandrew on 2011-07-23
> **pcastell said:**
> Make sure ~/.local/share/applications/mimeapps.list exist.
If the file is not there chromium will fail to set it self as default browser.

```

mkdir -p ~/.local/share/applications
touch ~/.local/share/applications/mimeapps.list

```

This worked for me! thanks a lot :P

---

### Post by notfoundt on 2011-08-28
> **edm1 said:**
> Changing the setting in System Settings>Preferred Applications may work.

Did pretty good job for me,thanks dude :P

---

### Post by mxndrwgrdnr on 2011-10-07
I think the mimeapps.list is probably my problem, but for some reason either I don't have the right permissions or I'm doing something else wrong. Here are my commands and outputs


xxx@xxxxxxxx:~$ mkdir -p ~/.local/share/applications
mkdir: cannot create directory `/xxxx/xxxx/.local/share/applications': File exists

xxx@xxxxxxxx:~$ touch ~/.local/share/applications/mimeapps.list
touch: cannot touch `/xxxx/xxxx/.local/share/applications/mimeapps.list': Not a directory

Any ideas???

---

