---
title: "MPlayer Loop"
date: 2006-06-25
forum: General Help
---

### Post by Irony on 2006-06-25
Does anyone know how to set MPlayer so that its default play is loop?

---

### Post by Anduu on 2006-06-25
Open nautilus and enable showing of hidden files.

Go to the .mplayer directory in your home folder and open the file called "config"...create it if it isn't there.

Add the line:

```
loop=0
```

Save.

---

### Post by Irony on 2006-06-26
Excellent! Thank you, it now loops.

---

### Post by Anduu on 2006-06-26
Good stuff :) 

One little annoyance I found however is if you are watching streaming media from certain sites...you know the ones that load their little ad clip before your chosen clip plays...mplayer will loop the ad indefinitely and the clip you want won't play.

Not a huge issue but annoying none the less.

---

