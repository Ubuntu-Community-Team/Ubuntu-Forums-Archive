---
title: "Can't Shutdown Laptop"
date: 2011-09-07
forum: General Help
---

### Post by hadi2 on 2011-09-07
Recently my Ubuntu 10.04 has become unable to shutdown computer completely , 
when i press the shutdown button it does some work and then it hangs on the purple screen and i have to hold power button for 4 seconds to shut it down . Where should i check to see what the problem is ? Maybe some service refuses to stop , i don't know 

thanks

---

### Post by Beacon11 on 2011-09-07
Check dmesg, /var/log/syslog, and /var/log/messages for errors.

---

### Post by hadi2 on 2011-09-08
I've checked those files but i can't find anything useful in those files , i have tried many suggestions from other sites such as removing plymouth themes or removing nvidia driver but nothing seems to work . What happened all of a sudden ? any ideas ? 
I have the same problem with suspend

---

### Post by hadi2 on 2011-09-08
I've realized that networking is disabled after i start Ubuntu again and i have to enable networking , maybe something is wrong with networking . i tried turning off wireless card and removing "wl" module before shutdown but that didn't help .

---

