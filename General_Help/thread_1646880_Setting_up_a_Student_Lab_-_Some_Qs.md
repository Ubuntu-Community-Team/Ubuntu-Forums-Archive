---
title: "Setting up a Student Lab - Some Qs"
date: 2010-12-16
forum: General Help
---

### Post by Sternfan on 2010-12-16
Hi all,

Every year or so I tinker around with the idea of changing one of the school labs (I am the network admin) from XP to Ubuntu.  I would like to give this a shot during downtime over the holidays, depending upon whether or not I can get the following:

I need to create a school lab of about 12 computers for a number of students to share.  The students have behavioral issues that require the PCs to be locked down with the following:

•	Students use one username (student) with a password that they all know.  This will be the same for every PC.  Everything related to the student account must be the same on every PC.
•	This password cannot be changed by the students (or expire.)
•	The home folder will be mapped to network share.  All students will share the same home folder at the same time.
•	Menus and panels need to be edited so that the students only see the programs that they need.  Once done, the menus and panels need to be locked so the students cannot change them.  Desktop backgrounds and screensavers also cannot be changed.
•	Firefox - set homepage and proxy settings (these cannot be changed).  
•	The student account can only be active between 7am and 9pm.  At the end of the day (9pm) the user account must be logged off.

In the past I have used windows group policy and **mandatory roaming profiles** (and some freeware to force logoffs) to accomplish this in an XP lab.

Thanks for any and all help,
Rob

---

### Post by drdos2006 on 2010-12-16
Normally Ubuntu requires an administrator user and password at installation. The administrator would have an administrator password.

From the system > users and groups you would add the users with a user password. Any programs to be installed or un-installed need the admin password. Remove all programs that are not needed with your admin password. Students log in with their login name and login password but do not have administrator rights unless you grant them in the users and groups settings.

regards

---

### Post by Sternfan on 2010-12-24
Thanks for the reply.

That really doesn't work however.  What ends up happening is the students mess with the account - make an obscene picture the desktop background, change the homepage to something else, change web settings to avoid the proxy (have to record all websites the students visit), change the password etc.  

Thanks,
Rob

---

