---
title: "Total System Crash"
date: 2009-11-23
forum: General Help
---

### Post by ~Niebr~ on 2009-11-23
Alright, so i was trying to install package files for ubuntu 9.10, i was getting an error stating there was a lib file conflict and that to fix it, a previous lib file needed to be removed in order for the next one to be installed, so without thinking, i removed that file, not knowing that its dependencies was the entire system, i think it was libcups2 or something like that, well anywho, i couldnt stop the removal, so i panicked and hard shut down the system, started is back up, i have no networking, no GUI interface, its basically a terminal right now, i was thinking of using a ISO disc to go into the recovery and fix it, would this be a good idea? or is that my only option at this point ?

---

### Post by teward on 2009-11-23
> **~Niebr~ said:**
> Alright, so i was trying to install package files for ubuntu 9.10, i was getting an error stating there was a lib file conflict and that to fix it, a previous lib file needed to be removed in order for the next one to be installed, so without thinking, i removed that file, not knowing that its dependencies was the entire system, i think it was libcups2 or something like that, well anywho, i couldnt stop the removal, so i panicked and hard shut down the system, started is back up, i have no networking, no GUI interface, its basically a terminal right now, i was thinking of using a ISO disc to go into the recovery and fix it, would this be a good idea? or is that my only option at this point ?

i'm guessing reinstallation/recovery is your only option, but I don't know.

---

### Post by ~Niebr~ on 2009-11-23
thats what i thought, i figured if i cant even latch onto a network to be able to install the gksu line then i wont even be able to do anything, unless ubuntu pulls files the repo,

---

### Post by lidex on 2009-11-23
Use your LiveCD. Boot up with it and choose the recovery/repair/fix option (can't remember exact wording). Should be able to get networking up. From there drop to terminal and try 
```
sudo apt-get install ubuntu-desktop
```

If not and you have separate /home partition, you can re-install without losing your user directory.

---

### Post by ~Niebr~ on 2009-11-24
well i was actually able to just install ubuntu on a new hard drive, and then ill just F disk my old drive and get all my stuff from there, but im having problem connecting to a wireless connection now, im in range of a router i know i am, and i set the SSID, but theres no option to connect to the SSID that i set,

---

### Post by lidex on 2009-11-24
I would recommend using "thread tools" at  top of first post to mark thread solved. Then post a new thread topic for your latest issue in the appropriate area of the forums.

---

