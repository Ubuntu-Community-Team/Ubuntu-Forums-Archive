---
title: "Time settings problems"
date: 2010-08-22
forum: General Help
---

### Post by LG83 on 2010-08-22
Hi,

I'm using Ubuntu 10.04, and there is some strange and annoying issue about my time settings:

I go to system -> administration -> time and date, click the lock to make changes,enter password, and set the time correctly (the configuration field is set to manual).Then I click "prevent changes" and close afterward....for a few seconds the time settings at the system tray seem correct, and then all of a sudden they return to their previous state!
I want to have the option to set my clock manually and not through a  server.


Does the problem I described sound like a bug or maybe I'm doing something wrong here?

Thanks.

---

### Post by AlphaLexman on 2010-08-22
Have you tried setting the time from your BIOS?

---

### Post by LG83 on 2010-08-22
I've read a bit about setting to bios, but I can't get it done.
Trying to change the date through the terminal (writing "date 08230123")gives me a message -  date: cannot set date: Operation not permitted.

Btw, should UTC in my rcS file be set to "yes" or "no"?

---

### Post by Vaphell on 2010-08-22
depends - if you want have bios set to utc and have local time in your system calculated with time zone difference then utc=yes, if you want to have bios and system set to local time then no.
In theory utc=yes is better because system leaves the bios clock alone and you can have many systems that play nice with each other. Unfortunately winXP for example treats bios as a local time and will always try to fix it, then ubuntu comes along and sets again to utc, wash rinse repeat. In such scenario it's better to forget about utc=yes because it will be an endless hassle.

---

### Post by LG83 on 2010-08-22
Btw, I didnt mention I run ubuntu via virtualbox...does it matter?

---

### Post by Vaphell on 2010-08-22
what system is the host?
i think i'd set ubuntu to utc=no

---

### Post by LG83 on 2010-08-22
windows xp is the host...I  tried with utc  both yes" and "no" ,it doesnt seem to do the trick.

---

