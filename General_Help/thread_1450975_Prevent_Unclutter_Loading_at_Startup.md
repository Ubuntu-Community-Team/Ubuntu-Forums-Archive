---
title: "Prevent Unclutter Loading at Startup"
date: 2010-04-09
forum: General Help
---

### Post by CTenorman on 2010-04-09
Hi,

I'm trying to find a way to prevent unclutter loading at startup.

When I want t watch flash videos full-screen, I zoom using compiz to the size of a smaller flash window until it fills the screen, which greatly improves the framerate. However, when I do this I like to hide the mouse, and use unclutter to do it. However, I don't watch videos most of the time and would prefer to leave unclutter off until I need it.

Does anyone know a way to make it just run when I load it at the command line? Thanks!

---

### Post by bashologist on 2010-04-10
The unclutter.postinst that comes with the source and it suggests that /etc/default/unclutter is what you want.

This should fix it...
```

sudo perl -p -i.bak -e '/START_UNCLUTTER/ and s/true/false/ or s/false/true/' /etc/default/unclutter && \
diff /etc/default/unclutter{,.bak} | perl -n -e 'print if s/^<\s+//'

```

The above script will toggle the startup option thingey... <3 perl

Also you might wanna try mplayer /tmp/Flash* for flash videos. That's how I do it. Gl hf.

---

### Post by CTenorman on 2010-04-10
Wow, great stuff, thank you!!

---

