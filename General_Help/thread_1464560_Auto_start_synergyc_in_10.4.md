---
title: "Auto start synergyc in 10.4"
date: 2010-04-28
forum: General Help
---

### Post by bshosey on 2010-04-28
I know 10.4 is not final but I am running it and loving it.
I am trying to have synergyc start and be working at the logon box of ubuntu 10.4. I can get it to autostart after the user is logged in. But I want it to be working before the user is logged in. Does anyone know how I can do this with 10.4

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
Call it from /etc/rc.local

---

### Post by bshosey on 2010-04-29
This did not work. Is there any other ideas.

---

### Post by bshosey on 2010-05-08
Bump!

---

### Post by bshosey on 2010-05-18
Bump

---

### Post by bshosey on 2010-05-30
Bump

---

### Post by bshosey on 2010-06-08
Bump

---

### Post by darkdragn on 2010-06-08
Have you looked here?
[http://synergy2.sourceforge.net/autostart.html](http://synergy2.sourceforge.net/autostart.html)
Or you could throw together your own start script, and treat it like a service... just dropping the script in init.d and linking it to rc2.d

---

### Post by bshosey on 2010-06-11
I did follow that link but no avail

---

### Post by bshosey on 2010-06-13
OK. I have two laptop with synergy. one works fine with just adding to the end of /etc/gdm/Init/Default file before the "exit 0" line

synergyc "host name of server"

The problem I am is the once I log into the computer that has dual monitors the curser will not span across the monitor. But if I do a sudo killall synergyc and then rerun synergy it works fine. So what I need to do is find a way to close synergy after I get logged in and the auto start it with dual monitors enabled.

---

