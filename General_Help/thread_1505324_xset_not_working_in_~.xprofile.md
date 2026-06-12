---
title: "xset not working in ~/.xprofile"
date: 2010-06-09
forum: General Help
---

### Post by gmatt on 2010-06-09
I have ubunutu 10.4 and I have in my ~/.xprofile

```

#!/bin/sh
xset r rate 180 30

```

this should set my keyboard rate to much quicker than the default. This is important to me because I'm very peculiar about my keyboard rate. If its off, I get annoyed very quickly. 

I can execute the command 

xset r rate 180 30

fine in any terminal and it works, but it doesn't work at startup, Any ideas why?

---

### Post by gmatt on 2010-06-09
Well the problem is that the gnome-settings deamon starts *after* xset is already executed, hence overwriting the settings I want.

To disable this use gconf-editor 

apps>plugins>keyboard

and disable this.

---

