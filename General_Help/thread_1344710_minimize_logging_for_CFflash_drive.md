---
title: "minimize logging for CF/flash drive"
date: 2009-12-03
forum: General Help
---

### Post by SSzretter on 2009-12-03
Is there a guide/article , or can people give me advice as to what I can do to minimize logging and/or use syslog to another machine to minimize writes to a flash drive / compact flash that I am using to boot ubuntu so I can extend the life of the CF?

---

### Post by hwttdz on 2009-12-03
Well to start with you can add noatime and nodiratime to your fstab.  

I don't remember the logging, but you could probably set a bunch of programs which log individually to log in different places, and could possibly set some of them to log to /dev/null, though then you of course wouldn't have any log. 

Secondly this was a bigger issue in years past as the number of writes has expanded by orders of magnitudes in the last 5 years or so.  It's getting to the point that if you were to peg the i/o your machine (and probably you) would die before the flash drive, i.e. 10's to 100's of years of continuous writes before failure.

---

