---
title: "HELP tryed removing libsqlite3-0 ubuntu went random app remove crazy"
date: 2011-06-19
forum: General Help
---

### Post by mindgernade on 2011-06-19
I was fixing dependency's and I typed apt-get remove libsqlite3-0 and it went crazy and started uninstalling applications like firefox and open office and several others, Im not even sure of the damage yet. I want to know what went wrong and why did this responded this way.

---

### Post by ajgreeny on 2011-06-19
It looks as if you have removed just about all of your desktop environment applications and many other things as well (gnome?)```
sudo apt-get install ubuntu-desktop
``` should put it right and get you back to a GUI if that is your problem.  If anything else is still missing you ought to find it easily in the dpkg log file **/var/log/dpkg.log** and can then install it again.

---

### Post by mindgernade on 2011-06-19
Thank you so much!

The log let me see how bad the damage was, but it removed to much to go through it by hand and the sudo apt-get install ubuntu-desktop set it strait it seems. My big question is why did removing that dependency cause it to start removing other software, apt-get should not had done that without asking first. I had no funny switches telling it to remove associated software.

---

### Post by mindgernade on 2011-06-19
Ok so I did some investigation and I tryed removing the libsqlite3-0 again but using software center and it prompted me to remove a few programs and I was ok with those but it did not warn me about all the other software it wanted to remove such as open office, Software center, chrome and several others. I think this is a bug were should I report this? apt-get and the software manager refuse to prompt for the other software.

---

