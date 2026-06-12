---
title: "Shutdown, Logout, Restart ... 60 sec time"
date: 2009-08-19
forum: General Help
---

### Post by oaxacamatt1 on 2009-08-19
Greetings,

Is there a way to shorten the Shutdown timing?  I found the shutdown time of 60 sec. to be very very long.  I would like to change it something reasonable like 3-5 sec.

Cheers,
M

---

### Post by dlmarti on 2009-08-19
It really depends on the number of services you are running.  Each one is sequentially "downed".

Check which services you are starting, make sure they are the only ones you need (both in your gui and system).

Then check to make sure your system doesn't have a bunch of down scripts laying around.

Personally I think 3-5 seconds is a little bit of an unreasonable goal.

---

### Post by dumblebee100 on 2009-08-19
> **oaxacamatt1 said:**
> Greetings,

Is there a way to shorten the Shutdown timing?  I found the shutdown time of 60 sec. to be very very long.  I would like to change it something reasonable like 3-5 sec.

Cheers,
M

why dont u try command to reach your goal ..if all you need is a fast shutdown then do it via command prompt 

```
sudo /sbin/shutdown -h now
```

if you really want the graphical dialouge then you have to change the gnome-session code ..which is not that simple ..so at present stick with command

---

### Post by Poodle Doodle on 2010-03-22
Actually that is not what he asked, so if you don't know, don't tell us.

Me thinks the 60 second off cycle is too long. 


Me thinks OFF means OFF and not "In a little while".



As in 44 magnum hand gun into Toyota Prius engine block, via the dash board and CPU.

"When I say stop, I mean stop"..... "Booyah, Booyah, Booyah, Booyah"

Toyota Prius stops.


Same thing with computer.

Me thinks 5 seconds for reconsideration tops.

Anyone have THE answer to this?

---

