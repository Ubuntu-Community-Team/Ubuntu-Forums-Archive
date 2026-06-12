---
title: "Ubuntu restarts itself"
date: 2009-11-27
forum: General Help
---

### Post by liorbalmas on 2009-11-27
Hi 
It is about three weeks thay my Ubuntu (Hardy) retarts itself once every 2-4 days.
It started after a big update I installed. 
(I am running a server kernel)
I didn't set any scheduled task for this.
I tried to look for the cuase in the logs but didn't find anything
 
Thanks

---

### Post by byStanderone on 2009-11-27
...before anything else, chek on your power line, plugs in particular, there might only be something loose or corroded.

---

### Post by ajgreeny on 2009-11-27
Also check for any possibility of the system, and cpu in particular, overheating.  You could try ```
sudo apt-get install  mbmon
``` for a temperature check, if it works with your mobo.  It seems unlikely on a server, but worth looking.

---

