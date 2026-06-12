---
title: "sound issue - driving me crazy"
date: 2009-06-30
forum: General Help
---

### Post by Zenze on 2009-06-30
Hello,

So I'm not a complete noob to linux/ubuntu. I have been using it for a while for many different things, including using the server edition to run a home file server.

However, on my desktop I have always had a sound issue on my desktop that I have never been able to fix no matter what I try. Everything will be working fine, music, movies, flash all are working great. But after either a restart or a restore from suspend no sound works :confused:. But if I reboot the computer again everything works again.

I can think of no reason why this would happen, but it is getting very annoying now that I am using my desktop again. Anyone have any advice/help? I am at a loss...

Thanks,
Z.

---

### Post by upbeat.linux on 2009-06-30
Which ubuntu release?

Try:

```
sudo killall -9 pulseaudio; pulseaudio >/dev/null 2>&1 &
```

---

