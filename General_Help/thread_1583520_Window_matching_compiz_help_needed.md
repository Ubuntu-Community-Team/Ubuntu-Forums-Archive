---
title: "Window matching compiz help needed"
date: 2010-09-28
forum: General Help
---

### Post by cadcam on 2010-09-28
so, i have my compiz file all setup and i love it.  there is JUST ONE THING......

i have the general opacity set to 94, which is perfect.  I applied to all windows using the command "class= "  .  

Whats wrong with this, is that I don't want it to opacify gimp and firefox.  i've tried
"class= $ !class=firefox"  and variations of it, but I can't seem to get it to exclude things.

any thoughts?

thank you.
A.

---

### Post by Tiede on 2010-11-04
Firefox windows are a little bit different than the others.
what you need is:
```

iclass=firefox & type=Normal

```
to match a Firefox window.

notice the **i** before the class name.

---

