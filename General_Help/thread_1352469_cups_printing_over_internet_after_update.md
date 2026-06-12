---
title: "cups printing over internet after update"
date: 2009-12-11
forum: General Help
---

### Post by keithclark on 2009-12-11
I had my computer allowing printing over the internet before I upgraded to 9.10, but now it does not work anymore.

I have turned on access via internet in the cups administration.

I am trying to see if the cups server is on by System>Administration>Services, but I now get:

Failed to execute child process "services-admin" (No such file or directory)

This also used to work before the upgrade.

Any help would be appreciated.

Keith

---

### Post by Woody1987 on 2009-12-12
The services option no longer works in karmic as the way services are handled has changed. Trying running ```
sudo /etc/init.d/cups start
``` in a terminal to start cups if it isnt already working.

---

### Post by keithclark on 2009-12-12
Cups is running.  What replaced System>Administration>Services?

Keith

---

