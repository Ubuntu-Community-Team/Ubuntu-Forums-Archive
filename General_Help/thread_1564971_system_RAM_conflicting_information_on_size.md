---
title: "system RAM: conflicting information on size?"
date: 2010-08-31
forum: General Help
---

### Post by rawlins02 on 2010-08-31
lshw suggests 8GB RAM on my system, which is what I ordered. But 

/proc/meminfo
free
system>administration>system monitor 

all show 3.2 GB memory.  Does this make sense?

---

### Post by andrewthomas on 2010-08-31
Are you running 32 or 64-bit?

---

### Post by rawlins02 on 2010-08-31
Running 32 bit

---

### Post by amendt on 2010-08-31
You should have installed the 64 bit version. If you want to use 8Gigs of ram

---

### Post by rawlins02 on 2010-08-31
Thanks. 

I've set up my system as dual boot. Windows 7 is 64-bit.  Under linux, what, briefly, are the most obvious performance advantages 64 vs 32-bit, given that I have 8GB RAM?  This machine is used mostly at work where I do FORTRAN programming and earth science research.  I've always been told CPU speed is most important for running FORTRAN executables (modeling), etc.

In my downtime I occasionally watch baseball and hockey games.  Fullscreen Flash 10, as many have observed, is rather choppy. 

Now to research the pros/cons...

---

### Post by inso_741 on 2010-08-31
32bit kernel can address a max memory of 4GB a lil of which is reserved for memory mapped io....if you want to utilise all the ram you bought you have to go with a 64bit OS

---

