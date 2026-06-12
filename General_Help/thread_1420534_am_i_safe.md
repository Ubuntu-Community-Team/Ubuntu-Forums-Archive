---
title: "am i safe ?"
date: 2010-03-03
forum: General Help
---

### Post by ctrlmd on 2010-03-03
hi 
everytime it try to write NETSTAT it display this result and i don't know what does it mean since im just a linux beginner NOTE: i replaced the ports with 00000 

[http://pastebin.com/rBRDB6qq](http://pastebin.com/rBRDB6qq)

---

### Post by spiderbatdad on 2010-03-03
try running netstat with some options like: 
```
netstat -atn
```
What you see in your previous output are hardware and local connections your machine uses internally.
What you are looking for is established external connections on specific ports like 6667...assuming you have not started your irc client...you might ask, why is it running?
Have a look here for better explanation.
[http://www.dti.ulaval.ca/webdav/site/sit/shared/Librairie/di/operations/informatique/windows/netstat_results.htm](http://www.dti.ulaval.ca/webdav/site/sit/shared/Librairie/di/operations/informatique/windows/netstat_results.htm)

---

### Post by ctrlmd on 2010-03-03
> **spiderbatdad said:**
> try running netstat with some options like: 
```
netstat -atn
```What you see in your previous output are hardware and local connections your machine uses internally.
What you are looking for is established external connections on specific ports like 6667...assuming you have not started your irc client...you might ask, why is it running?
Have a look here for better explanation.
[http://www.dti.ulaval.ca/webdav/site/sit/shared/Librairie/di/operations/informatique/windows/netstat_results.htm](http://www.dti.ulaval.ca/webdav/site/sit/shared/Librairie/di/operations/informatique/windows/netstat_results.htm)

so there is no risk here about anything external that could harm my machine 
because im not running anything

---

### Post by doas777 on 2010-03-03
well, they look like dbus and esd connections so you should be fine. they both use local tcp ports for communication with the processes that use them.

---

### Post by ctrlmd on 2010-03-03
thanks all

---

