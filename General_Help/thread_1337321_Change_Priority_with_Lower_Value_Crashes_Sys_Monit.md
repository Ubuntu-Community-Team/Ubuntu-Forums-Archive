---
title: "Change Priority with Lower Value Crashes Sys Monitor"
date: 2009-11-25
forum: General Help
---

### Post by the_guv on 2009-11-25
.. well, that's it really!

For instance, I open System Monitor, right click, say, Skype and choose Change Priority.

If I set a higher value (so a lower priority) then Sys Monitor is happy.  But set any lower value (higher priority) and Sys Monitor crashes and, opening up Sys Monitor again, the value is as it was originally.

Am mainly using Jaunty on this machine.  No idea if this is an issue with Karmic.

??

---

### Post by raktarok on 2009-11-25
I think you can increase the priority of a process only with root privileges. Try doing this:

```
gksudo gnome-system-monitor
```

Alternatively, use renice from the terminal without sudo, and see the output.

---

