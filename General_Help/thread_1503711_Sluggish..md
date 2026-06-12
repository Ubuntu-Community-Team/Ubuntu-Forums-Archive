---
title: "Sluggish."
date: 2010-06-07
forum: General Help
---

### Post by Colo2 on 2010-06-07
Hello 

I was wondering if I could have some advice.

I have this old'ish PC with ubuntu on it. But since I installed it, it seems pretty sluggish and slow. It's usable, but when I have about 6 or 7 applications open, it takes ages to maximise and minimise applications, the system freezes then unfreezes, then my music stops playing and skips, then starts again. Basically like a general overload.

The processor is a P4 3.00GHz
It has 512MB of RAM

This computer previously worked absolutely fine with Windows XP. I can't see any reason for it to have problems on ubuntu?

Also, I've not done anything to slow ubuntu down, All I've done is changed the DT background, changed the theme and adding different icons. No desktop effects enabled etc.

Thanks

---

### Post by Colo2 on 2010-06-07
[IMG]http://i47.tinypic.com/117fm0o.png[/IMG]

---

### Post by Colo2 on 2010-06-07
...

---

### Post by oldos2er on 2010-06-07
Which version of Ubuntu are you using? If you're running Gnome, you might want to try a lighter desktop environment e.g. xfce or lxde.

If possible, I would bump up the RAM to 1GB. 

You can tweak the vm.swappiness setting, see [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by snowpine on 2010-06-07
It sounds like your computer is going into "swap" based on your "with several applications open at once, switching apps is slow" observation. Your hard drive is much slower than RAM, so it's best to reduce swap use by following the link in the previous post.

512mb is the bare minimum for Ubuntu. I recommend upgrading your RAM and/or lowering your RAM usage (for example by using fewer applications at the same time, or switching to a lightweight interface like LXDE).

---

