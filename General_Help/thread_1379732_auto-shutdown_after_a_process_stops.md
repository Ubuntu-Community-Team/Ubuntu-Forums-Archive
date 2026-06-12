---
title: "auto-shutdown after a process stops?"
date: 2010-01-12
forum: General Help
---

### Post by drooze on 2010-01-12
in windows I have this little program called "poweroff". I use it to shut down my pc after vlc stops playing a movie. I set vlc to shut itself down after playing, and then the program starts a countdown to shutdown the pc.
is there a similar program for ubuntu? could this be achieved through the command line?
I'd like it to give me little warning period though, where I still have the option to cancel.

Can anybody help?

---

### Post by drooze on 2010-01-13
nobody? This can't be that hard to do?

---

### Post by Grenage on 2010-01-13
I haven't seen gui software for it, but that should be easy enough to script.  For example:

```
vlc && shutdown -h -P now
```

When vlc terminates, it would advance to the shutdown command.  You cane use the *TIME* parameter with *shutdown* in order to give you some grace.

---

