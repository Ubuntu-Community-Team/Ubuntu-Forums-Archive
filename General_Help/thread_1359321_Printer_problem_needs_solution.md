---
title: "Printer problem needs solution"
date: 2009-12-19
forum: General Help
---

### Post by sigurnjak on 2009-12-19
Until today my Brother printer was working perfectly . As of today i have a problem  Cups not starting at boot and printer not connecting .
So far temporary solutions to  issue this command when i wish to print  ;
 sudo /etc/init.d/cups restart

However after rebooting it does not work and i have to go back to terminal.
Does anyone have a more permanent solution ?

---

### Post by Sin@Sin-Sacrifice on 2009-12-19
There should be a spot for cups in System>Preferences>Startup Applications.

---

### Post by sigurnjak on 2009-12-19
I do not see one . What do you have  for cups in start up apps ?

---

### Post by falconindy on 2009-12-19
You'll want to look at the bootup logs to see why CUPS isn't loading.

---

### Post by sigurnjak on 2009-12-19
Here is error log , if someone can decipher it

---

### Post by Leppie on 2009-12-19
have you tried the cups admin page?
open your web browser and go to [http://localhost:631/](http://localhost:631/)

---

### Post by sigurnjak on 2009-12-20
Yes i did . At first i could not connect. But after issuing  sudo /etc/init.d/cups restart i did log in , added a printer and all was well. Then i rebooted and no go . 
Funny thing is once i tell it to restart it prints fine , it only does not seem to start at boot time .

---

### Post by sigurnjak on 2009-12-20
Well , i believe i have it solved . I know it is not most elegant , but rather brute solution  and i still do know what caused it  but it is solved . I completely uninstalled anything and everything related to cups including cups , hunted down all cups folders in the system and home folder, reboted  and reinstalled cups and needed dependencies . 
That is it . It works like before , and it survived 2 reboots so far .

---

