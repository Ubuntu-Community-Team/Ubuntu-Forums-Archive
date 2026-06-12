---
title: "TIMED shutdown?"
date: 2010-05-01
forum: General Help
---

### Post by dzwestwindsor on 2010-05-01
I'm running 10.04, and i like how in Karmic, there was a timed shutdown. meaning that once i hit "Shutdown" it would count 60 seconds (or however long) b4 it shut, and i could abort anytime withen that period. how can i do tat in lucid? Thanks

---

### Post by shtripok on 2011-05-03
Is it possible for 11.04?
Maybe, 3rd party utility?

---

### Post by andrewthomas on 2011-05-03
In the terminal 
 
```
 
sudo shutdown -h +(how many minutes til shutdown)

```

---

### Post by shtripok on 2011-05-04
No-no, sorry I was not clear.
I don't need "just shutdown after delay".

I need "shutdown after I press power button on my pc, or choose "shutdown" in gnome menu"

Currently after that pops a window with some buttons: "shutdown", "standby", "hybernate", "reboot" (not sure list complete equal, but it's not mean). 
Then I have to press one of that button to begin a shutdown.

Previously one of this action can be settable as default, and countdown starts. In case of no action default was performed after timeout, and no additional choose was requested.

**I want to return that behavior: a countdown timer in default shutdown action button.**

---

### Post by shtripok on 2011-05-14
up

---

