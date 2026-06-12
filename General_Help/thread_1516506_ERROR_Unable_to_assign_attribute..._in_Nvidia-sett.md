---
title: "ERROR: Unable to assign attribute... in Nvidia-settings"
date: 2010-06-23
forum: General Help
---

### Post by MechWarrior001 on 2010-06-23
I'm trying to set graphical settings like AA, AF and Vsync in Nvidia-settings however they don't stick, all I get is a error like this
```

ERROR: Unable to assign attribute XVideoSyncToDisplay specified on line 52 of
       configuration file '/home/tremded/.nvidia-settings-rc' (no Display
       connection).

```

and I have to manually reset them to desired values after every login. Is there a way to make them stick when logging in/out?

---

### Post by spcwingo on 2010-06-23
I had a similar problem...I couldn't get my settings to stick in between boots.  I just edited the menu entry under system>admin>nvidia by adding gksu to the front end of the command.  Everything now works like a charm.  ;)

---

