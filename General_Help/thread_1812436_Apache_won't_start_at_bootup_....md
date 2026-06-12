---
title: "Apache won't start at bootup ..."
date: 2011-07-26
forum: General Help
---

### Post by dabayliss on 2011-07-26
I have a new Ubunto Desktop (downloaded Friday) and have installed Apache. Everything works beautifully - provided I start Apache myself. I cannot get it to start automatically at bootup.
 
I did the normal 'googling' - Apache2 IS in my rc files - with a level of S91 in run-level 2. I tried using the 'BUM' - and it shows that Apache2 IS active - and yet the service shows as not-started. (I can start it from BUM - but after reboot it is stopped again)
 
I'm sure there is something I am missing here - anyone got any clues ....

---

### Post by 2F4U on 2011-07-26
Did you look into the log files. There may be error messages that provide hints on where the problem lies.

---

### Post by dabayliss on 2011-07-26
Upon system reboot nothing happens to the logs in Apache2 (when I start by hand the apache2 error log just says 'resuming normal operations' - and things work)
I checked boot.log, kern.log and syslog - none of them mention apache (or even *apa*)

David

---

