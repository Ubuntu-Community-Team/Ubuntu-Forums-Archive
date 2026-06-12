---
title: "Clock always hour behind on restart"
date: 2006-06-09
forum: General Help
---

### Post by ScottY86 on 2006-06-09
I just upgraded to Dapper a few days ago.  Ever since then, every time I restart my computer, my clock resets to an hour behind the actual time.  I go and click 'Synchronize Now' and it goes back to normal.  I have the time zone set correctly and when I type 'date' on the command line, it says PDT and not PST which I believe is correct.  

Any ideas?

Thanks!!!
Scott

---

### Post by kthakore on 2006-06-09
Your clock is begin synchronized to the wrong time zone, (happens because of the ambiguity of the ip address) anyway, just right click on the clock , choose Adjust Date and Time, and uncheck periodically snyc with internet servers. If this doesn't work, change you time and when shutting down check the keep changes box.

---

### Post by pyromithrandir on 2006-06-09
It might be syncing to your BIOS time setting, which could be off. Next time you restart, go into your BIOS setup and see if the time there is set right.

---

### Post by Chris03 on 2006-06-09
I had a problem before where my clock kept appearing 5 hours behind. It was due to the UTC time format. What you can do is this:

sudo gedit /etc/default/rcS

Make sure UTC=no

---

