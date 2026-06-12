---
title: "Problems with disabling the restoring of a session when startning Ubuntu"
date: 2009-08-19
forum: General Help
---

### Post by rob4jp on 2009-08-19
Hi Ubuntu users

I have a problem in Ubuntu (9.04, 64 bit). 

Sometime ago I activated the option "Automatically remember running applications when logging out", which is available in the "Startup applications preferences", from the System->Administration menu. 

However, it never worked well, since it only started up some of the programs, and seemingly placed the automatically started programs on random virtual desktops, and most of the time without remember e.g. which files were opened in the applications, etc.

So I inactivated this feature from the same place where I once activated it. However, ever since then, every time when start Ubuntu it seems to try to restore an old session and automatically starts up several applications from this old session. It have been several months now, and I still get these old applications every time I login.

Is there anyone who know about a simple way to reset the session that gnome (or whatever the responsible software is) tries to restore? 

Best regards,
Robert

---

### Post by rob4jp on 2009-09-07
I found the answer to my own question. I removed all the files in:

~/.config/gnome-session/saved-session/*

and now, finally, there are no old applications starting up when I login. 

I think this should be done automatically when the "Automatically remember running applications when logging out" option is deactivated...

Rob

---

### Post by alejaaandro on 2009-09-07
happy you sorted it out.. 
:)
please mark as "solved"

---

