---
title: "FreePops Updater not launching"
date: 2009-12-27
forum: General Help
---

### Post by jeannot_unbu on 2009-12-27
I have installed FreePops, from this site:
[http://allmyapps.com/app/ubuntu-9.10/freepops-updater-gnome-freepops-updater](http://allmyapps.com/app/ubuntu-9.10/freepops-updater-gnome-freepops-updater)

But when I try to launch it (by the way the apps is showing in Applications => System Tools) this is the error message I am getting:

Could not launch FreePops updater
Failed to execute child process  "su-to-root" (Not such file or directory)

Anyone to help me to have FreePops working and setting it up to read my Hotmail emails? 
Many thanks

JC

---

### Post by zaflaucich on 2009-12-28
Edit the command of the menu from:

su-to-root -X -c freepops-updater-zenity

to:

gksu freepops-updater-zenity

---

### Post by jeannot_unbu on 2009-12-28
Thanks for that, though I am giving up reading my emails from Hotmail using Evolution or THunderbird as it mess up my emails. When I open by Hotmail account on my XP machine, the contents of the mailbox is different from the one in Thunderbird or Evolution. Emails are being removed from the inbox without me doing anything, a bit unnerving for me as I have sometimes to keep some important emails.
JC

---

