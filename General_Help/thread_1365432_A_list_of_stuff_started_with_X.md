---
title: "A list of stuff started with X?"
date: 2009-12-27
forum: General Help
---

### Post by RabidSpatula on 2009-12-27
In short:
In 9.10 x64, how can I get a list of things that start/restart when I do an X "zap" via ctl-alt-backspace?

I know I can get a partial list from settings->preferences->startup and from my .profile, but there's obviously more involved in the process than that.


Why:
I'm trying to solve a video playback bug. When the system is freshly booted, there's no problem. After time progresses, video playback gets sticky (stops, lurches forward, stops again), then eventually it dies completely. I've tried a previous kernel, I've tried new codecs, nothing works except a reboot or an X restart. This strongly indicates there's a bug somewhere, but I can't know where until I've gone down the list of things that get restarted and manually restart each as a test.


Thus:
How can I get a list of everything that's loaded/reloaded/started/restarted from an X zap?

Thanks

---

### Post by dcstar on 2009-12-27
> **RabidSpatula said:**
> 
.......
How can I get a list of everything that's loaded/reloaded/started/restarted from an X zap?

Thanks
This should give you a starting point:
```
man startx
```

Also check that you have sufficient disk space for /tmp.

---

