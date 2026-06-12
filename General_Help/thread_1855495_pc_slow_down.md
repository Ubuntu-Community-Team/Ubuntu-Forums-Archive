---
title: "pc slow down"
date: 2011-10-06
forum: General Help
---

### Post by tobythedog on 2011-10-06
i have another problem with my pc and xubuntu 11.04 mp pc is an ols packard bell pent 4 1.6ghz  384mb ram , something is slowing the pc down realy badly for example i will click to open a new tab on the browser and sometimes it can take upto 30 sec for one to open , also the processor often goes to 100% usage and stays there for several minutes, is there some way i can find out what is causing the slow down

---

### Post by pr3zident on 2011-10-06
> **tobythedog said:**
> i have another problem with my pc and xubuntu 11.04 mp pc is an ols packard bell pent 4 1.6ghz  384mb ram , something is slowing the pc down realy badly for example i will click to open a new tab on the browser and sometimes it can take upto 30 sec for one to open , also the processor often goes to 100% usage and stays there for several minutes, is there some way i can find out what is causing the slow down

open the terminal and type the command "top" and look for %CPU - its going to tell you which program is taking up most of the compute processor...

---

### Post by collisionystm on 2011-10-06
Or install HTOP

htop is alot easier to read IMO

---

### Post by SeanTater on 2011-10-06
> **collisionystm said:**
> Or install HTOP

htop is alot easier to read IMO

+1 on htop. But your system monitor (or whatever the equivalent for Gnome might be) should also be able to sort by CPU. Whichever is the highest on the list is probably the issue. You can usually terminate the program to fix the issue but **be sure to save your work first** in case you kill off a program you need!

---

### Post by tobythedog on 2011-10-06
looked  on system monitor and there doesnt seem to be anything using to much processor power, however the machine is painfully slow to use, anyone got any ideas please.

---

### Post by jazzon on 2011-10-06
check your bios output at boot time...is your ram all there?  bad stick on a machine that old would do it.  Also is it running too hot?  If nothing is showing on top/htop/system monitor it is more likely hardware (although some kind of network lags could cause it too...)


Good luck.

---

### Post by tobythedog on 2011-10-06
thats interesting , i dont know if its anything to do with the problem but my opera browser keeps telling me it looks like i am on a slow network and asking if i want to use opera turbo, my broaband is about 3m download and 260 upload

---

### Post by tobythedog on 2011-10-12
changed the memory and its better but its still to slow really a pain to use, i have had this machine running really well with older version xubuntu is the latest version slower than a couple of versions ago

---

### Post by WorMzy on 2011-10-12
At a guess, you're running out of RAM. Firefox isn't exactly known as being RAM-friendly, and 384MB isn't a lot of RAM to begin with.

What does ```
free -m
``` say?

---

### Post by tobythedog on 2011-10-16
have upgraded to 11.10 and the pc is flying again.really didn't like 11.04 it drastically slowed the machine down.

---

### Post by tobythedog on 2012-08-11
put lubuntu on and the pc really flies now using far less memory to run lxde desktop and it works well, if you havent tried lubuntu i recomend you give it a go works very well for me.

---

