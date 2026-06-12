---
title: "Making apt cache permanent"
date: 2010-04-08
forum: General Help
---

### Post by sarin_cv on 2010-04-08
Hi... I don't want ubuntu to clean /var/cache/apt/archives directory automatically... is it possible to make it permanent by editing any conf file???

---

### Post by Barriehie on 2010-04-08
> **sarin_cv said:**
> Hi... I don't want ubuntu to clean /var/cache/apt/archives directory automatically... is it possible to make it permanent by editing any conf file???

I'm running debian so this should work, change:
```

APT::Archives::MaxAge "30";
```
to
```

APT::Archives::MaxAge "0";
```
in /etc/apt/apt.conf.d

Can also see the manpage for apt.conf

---

### Post by drs305 on 2010-04-08
It will work in Ubuntu. It's the 20archive file in the aforementioned folder (/etc/apt/apt.conf.d)

---

### Post by sarin_cv on 2010-04-08
should I change APT::Archives::MaxSize also?

---

### Post by drs305 on 2010-04-08
> **sarin_cv said:**
> should I change APT::Archives::MaxSize also?

Yes, if you plan on keeping a lot of packages by increasing the time they are retained you may want to increase the size as well.

If you are still running Jaunty, it wouldn't be as important as if you were running Lucid Beta, as Jaunty's updates would be far fewer and the cache would not build nearly as quickly.

---

### Post by sarin_cv on 2010-04-08
I am using Lucid beta now.. I am planning to make periodic backup of the apt cache...

---

