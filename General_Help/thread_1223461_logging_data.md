---
title: "logging data"
date: 2009-07-26
forum: General Help
---

### Post by ub007 on 2009-07-26
Hi all,

I've got an app which keeps logging and the logs keep rotating every minute.Theres a particular string in these logs that I'm interested in and wish to capture all lines that contain the string.Any ideas?

log file could be **smap.log**
string is 'RSS 1'
so I do a 
#pgrep "RSS 1" smap.log >> ub.log
so this would pipe all lines containg the 'RSS 1' string to ub.log.But the app keeps logging & logs would now rotate and how would i be able to pipe the next lines containg the string to ub.log.It needs to be appended and not replace the existing entries in ub.log....



If any one could help me with a script that could do the job???

Cheers
Davis

---

### Post by DaithiF on 2009-07-26
Hi, you could do:

tail -f smap.log | grep --line-buffered "RSS 1" >> ub.log

cheers
Dave

---

### Post by DaithiF on 2009-07-26
oh, add a & to the end of that command too, to make it run in the background

---

