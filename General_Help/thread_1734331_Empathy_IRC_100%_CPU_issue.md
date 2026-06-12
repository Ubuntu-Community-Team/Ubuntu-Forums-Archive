---
title: "Empathy IRC 100% CPU issue"
date: 2011-04-20
forum: General Help
---

### Post by PhonicLynx on 2011-04-20
I don't know if anyone else has had this problem. But in the past few days I've noticed that my CPU usage has been quite high... Then out of the blue 5 our of 8 cores would have near 100% usage and the computer was idle as far as I could see.

After doing some searching I saw that dbus-daemon was causing 90% CPU usage so I ran dbus-monitor where I saw the same output happen time after time after time. when I paused it.. it pointed to Empathy. Every now and then I'd see the process telepathy-idle just occasionally pop up and back down the process list. 

After uninstalling the package telepathy-idle all of that usage dissapeared.

Having said all this, I've not had Empathy installed for several months. I have un-installed Empathy and use Pidgin instead. 

Can any one shed some light as to why this would happen?
:popcorn:

---

