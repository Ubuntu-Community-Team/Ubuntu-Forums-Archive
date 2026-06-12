---
title: "Pidgin stopped working with error No GSettings schemas are installed"
date: 2012-05-22
forum: General Help
---

### Post by sunbird on 2012-05-22
I was using pidgin last night, no troubles. This morning, woke the computer from sleep and it was having trouble connecting, so I closed the program and relaunched it-- or rather, tried to relaunch it. Would not launch. Running from command line yields:

```
$ pidgin

(Pidgin:3137): GLib-GIO-ERROR **: No GSettings schemas are installed on the system
Trace/breakpoint trap (core dumped)

```

I tried purging all pidgin-related packages and reinstalling. No dice.

**Edit:** There was a custom apparmor setting that was causing the trouble. Sorry for the noise.

---

