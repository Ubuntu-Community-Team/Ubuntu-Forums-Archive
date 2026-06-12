---
title: "firefox status in system monitore - zombie"
date: 2006-04-28
forum: General Help
---

### Post by ubiwankanubi on 2006-04-28
Since I've installed ubuntu a few weeks ago, I've alway run into the problem that when I open a new window in firefox, or if a website opens a popup window, then the cpu usage goes haywire for a few minutes then it finally opens the new window.

I have tried running the system monitor, to see what the status is, and it showed that firefox-bin was zombie. other processes were sleeping. what's that mean, and how to fix it?

Also, when I start a program, it always seems to take a few seconds to initialize, before starting the program, then a few more seconds before the program's window opens up.

what gives? I'm using a 2ghz p4, so it shouldn't be too slow right?

---

### Post by Sef on 2006-04-28
How much ram do you have?

Open the terminal (Applications > Accessories > Terminal) and type free -m.  Then post the results.

---

### Post by ubiwankanubi on 2006-04-28
free -m
             total       used       free     shared    buffers     cached
Mem:           218        212          6          0          3         48
-/+ buffers/cache:        160         58
Swap:          956         86        870


Also, I checked, firefox-bin is using a whopping 156mb! why does it need so much?

---

### Post by bionnaki on 2006-04-28
firefox is nortoriously a resource-hog.

---

