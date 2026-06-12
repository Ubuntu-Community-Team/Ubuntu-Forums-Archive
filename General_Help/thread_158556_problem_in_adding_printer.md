---
title: "problem in adding printer"
date: 2006-04-11
forum: General Help
---

### Post by Knoob on 2006-04-11
When I go to System->Administration->Printing, and add printer, I get this error message:

"The Application "gnome-cups-add" has quit unexpectedly."

Can someone tell me what's going on?

Basically I want to add my printer (Epson PM 940C)
I'm using Ubuntu 5.10 (Gnome)

Thanks

---

### Post by Knoob on 2006-04-11
anyone?
help please ...

---

### Post by Miksdu on 2006-04-13
Yeah, I get the same message.

---

### Post by muzaki on 2006-04-16
me too, when adding printer, i can see my canon mp370 being recognized,but thats all ,i mean all freeze and getting the same message like above


UPDATE : I'm using turboprint to install driver for **canon mp370**.
but still i cant add printer from System->Administration->Printing nor printing anything:confused:  help needed

---

### Post by Najand on 2006-04-17
I have the same problem. But I cannot even open the "printing" application. Well, I was looking for an answer and I found one comment about it in a debian forum. and it is: uploading the Application "gnome-cups-add". I tried to do that. but was very unsuccessful when I got the same error message. Well, still very pissed off. Anyone has a clue?

---

### Post by biotim on 2006-04-17
I was able to add a printer by installing and running foomatic-gui.  I then had to use gnome-cups-manager to change the settings for the printer from "network printer" to "local printer".  It still didn't work though.  When I tried to print a test page (on my HP deskjet 960c) it just printed what appeared to be some postscript header information about the document.:-?

---

### Post by biotim on 2006-04-17
Success!  It looks like there's some kind of conflict with uim (see [http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg14910.html]("http://www.mail-archive.com/desktop-bugs@lists.ubuntu.com/msg14910.html")).  Just uninstall your uim packages before adding the printer with gnome-cups-add.   Then I think it's ok to reinstall your uim packages.

---

### Post by Knoob on 2006-04-19
yup, uninstalling uim packages solves the gnome-cups-add problem.

so now i can add printer via System->Administartion->Printing

However, I cannot find the driver for my printer among the list.
It detected my printer (Epson PM-940C) properly but there is no driver for it.
(In the list there is PM-930 but will this be ok?)

Or should I look for the exact driver from the web?
Problem is I dont know how to install a printer driver that I download from the web.

Anyine kind enough to show me the steps?

Thanks

---

### Post by muzaki on 2006-04-20
great info bout the bugs!!
now i can use my japanese desktop + my CANON printer just works like a charm !!
thanks

for Knoob:
> Problem is I dont know how to install a printer driver that I download from the web.
1. if you manage to find the official driver from net then it will be better to use that.For installation: read the README file or INSTALL file inside the package you downloaded or from the web itself
2. if dont, i think you can use the recomendation one(PM-930).See my printer, mp370 correctly detected,but no driver in the list though.So i use canon multipass c2500 which is older version than mp370.it works for color and b/w. still not able to get the scanning function and photocopy function to work though. now i'm trying other canon driver since nothing to loose

---

### Post by dmizer on 2006-04-20
you can configure your printer in english by going to [http://localhost:631/](http://localhost:631/) in your browser.  there's a fix for this particular bug, but i haven't gotten around to fixing it because browsing to cups in firefox works fine instead.

this allows you to retain your japanese input ability while configuring your printer in english.

---

### Post by Knoob on 2006-04-23
thanks to all those who replied.

anyway, i checked out the dapper beta release live cd, and my printer is now detected and the driver is supported out of the box!! 

i'll do the install when i find time. :D

---

### Post by Najand on 2006-05-09
[QUOTE=Knoob]yup, uninstalling uim packages solves the gnome-cups-add problem.

so now i can add printer via System->Administartion->Printing

However, I cannot find the driver for my printer among the list.
It detected my printer (Epson PM-940C) properly but there is no driver for it.
(In the list there is PM-930 but will this be ok?)

Or should I look for the exact driver from the web?
Problem is I dont know how to install a printer driver that I download from the web.

Anyine kind enough to show me the steps?

Thanks[/QUOTE]

You can find the suitable driver for your printer in the following page... Unfortunately it is just in Japanese. I have used it and downloaded the rpm package and it works perfectly for me.

[http://www.avasys.jp/linux/dl_ink.html]("http://www.avasys.jp/linux/dl_ink.html")

---

