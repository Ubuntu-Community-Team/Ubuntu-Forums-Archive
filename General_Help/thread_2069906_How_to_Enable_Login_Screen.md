---
title: "How to Enable Login Screen"
date: 2012-10-11
forum: General Help
---

### Post by dave r on 2012-10-11
After 4 years on Ubuntu I'm now running Lubuntu, installed it this afternoon, its running well but I need to enable the login screen, when I installed it I did so with automatic log in, I've now created the user accounts and want it to start and go to the login screen instead of straight through to my account. If I log out it will go to the login screen but if I start the computer  it just goes through to my accout.

---

### Post by sienile on 2012-10-11
You turn off Auto-Login through Settings > User Accounts.

---

### Post by dave r on 2012-10-11
> **sienile said:**
> You turn off Auto-Login through Settings > User Accounts.

Lubuntu 12.04 only has system tools - users and groups.

Is there an app I can install that gives me a GIU to change settings for the Login, or is it all done in the terminal?

---

### Post by ajgreeny on 2012-10-11
You probably need to edit the your lxdm.conf file using ```
gksudo leafpad  /media/Lubuntu/etc/xdg/lubuntu/lxdm/lxdm.conf
``` by commenting out the line near the top that says ```
autologin=*username*
``` then logout, or maybe a restart is needed.  I don't think there is a GUI app to do it for you.

---

### Post by dave r on 2012-10-11
> **ajgreeny said:**
> You probably need to edit the your lxdm.conf file using ```
gksudo leafpad  /media/Lubuntu/etc/xdg/lubuntu/lxdm/lxdm.conf
``` by commenting out the line near the top that says ```
autologin=*username*
``` then logout, or maybe a restart is needed.  I don't think there is a GUI app to do it for you.

The second line is #autologin=dgod
thats the only line with autologin in it, does that need changing? is there likely to be another file that also needs changing?

---

### Post by dave r on 2012-10-11
What I've found out is that there are two files to edit, lightdm and lxdm,

[http://askubuntu.com/questions/106428/how-to-disable-automatic-login](http://askubuntu.com/questions/106428/how-to-disable-automatic-login)

[http://askubuntu.com/questions/182274/how-to-disable-autologin-in-lubuntu](http://askubuntu.com/questions/182274/how-to-disable-autologin-in-lubuntu)

while I was searching the net I came accross both these threads, at first I just thought it was two ways of changing it, then I realised you need to edit both. Log in is now working.

---

### Post by ajgreeny on 2012-10-11
Whoops!

Yes, I forgot that this had changed since lightdm took over from lxdm.  It used to be just the one file that needed editing.

That's progress for you.

---

