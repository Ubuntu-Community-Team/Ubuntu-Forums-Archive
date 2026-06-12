---
title: "Adminisrative mode issues"
date: 2006-02-26
forum: General Help
---

### Post by Chemicalvamp on 2006-02-26
I have been having a problem when atempting to set the clock (right click on the clock, go to adjust time/date. input my password.. and nothing happens, and entering any type of administrative mode..(start) i click admin mode, i get the red border, i put my password in.. and instead of letting me modify anything it goes right back to the (start). Iam unable to access the internet untill i set up my network configuration.

When i try opening adept i get this:

DCOP Communication error (Adept)

There was an error setting up inter-process communications for kde. The message returned by the system was:

Authentication rejected, reason: none of the authentication protocols specified are supported and host based authentication failed

please check that the "dcopserver" program is running!

after i click okay Adept DOES come up... this just started recently i reinstalled kubuntu today and all was okay untill this started up

---

### Post by Jucato on 2006-02-26
The Administrative issue might be solved by upgrading KDE to 3.5.1.
As for Adept, I'm not sure about it.

---

### Post by Chemicalvamp on 2006-02-26
hmm ok lemme try it.

---

### Post by ironmaiden6669 on 2006-02-27
Sounds to me like you haven't enabled root to log on graphically.

Try this;

In Gnome
 Open System --> Administration --> Login Screen Setup 
 Click on the security tab 
 Check Allow root login

OR

In KDE
 Open Konqueror and open the /etc/kde3/kdm/ folder 
 Right click the kdmrc file and then Actions --> 'Edit as root' 
 On line 246 should be AllowRootLogin=false change it to 'true' 
 Save and exit.

---

