---
title: "Flash stopped working"
date: 2011-06-14
forum: General Help
---

### Post by sbelz79 on 2011-06-14
Flash had been working fine in both Chrome and Firefox until yesterday.  Now I get a message saying that it's out of date, but so far I haven't been successful with installing Flash 10.  First, I did the obvious thing and clicked "update plugin" which took me to the Adobe site.  I selected APT for Ubuntu 10.04 + (because I'm using Ubuntu 10.04).  After going through the quick installation process, I got the message "Package 'adobe-flashplugin' is virtual."  I restarted Chrome, and my Flash player was still out of date.  I tried to do the same thing in Firefox.  I found instructions elsewhere on the Ubuntu forums to try:
```
sudo apt-get remove --purge flashplugin-nonfree -y && sudo apt-get install flashplugin-nonfree
```

Which also did not solve the problem.

I am running Ubuntu 10.04 64-bit.  I primarily use the Chrome browser, though sometimes use Firefox (certain online flash games have only ever worked in that browser).

---

### Post by pqwoerituytrueiwoq on 2011-06-14
use the flash aid addon for firefox
google "flash aid"

---

### Post by sbelz79 on 2011-06-14
Thank you, kind human :-)  I ran flash aid in Firefox, and Flash now works in both Firefox and Chrome.

---

