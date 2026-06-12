---
title: "Chromium Incognito by Default in 11.10"
date: 2012-04-01
forum: General Help
---

### Post by residualbit on 2012-04-01
Hi all,

I've been able to do this in older versions (of ubutnu and chromium) with no issues, but can't get this working now.

In the past, it has just been a matter of adding "--incognito" to the launcher, but I can't get it to work now. I have tried editing
```
/usr/share/applications/chromium-browser.desktop
``` 
which by default shows 
```
Exec=/usr/bin/chromium-browser %U
```
to
```
Exec=/usr/bin/chromium-browser --incognito %U
```
with no luck. I've tried removing the %U, or moving it before the --incognito to no avail. Any ideas?

Thanks,
nak

---

### Post by residualbit on 2012-04-01
I forgot to mention that in any combination including "--incognito", when I try to launch chromium, nothing happens.

---

### Post by residualbit on 2012-04-01
adding --incognito does work.

What does not work however, is having the default behavior open the 'New Tabs Page' on launch. I picked an actual site to use as a home page and the edited launcher started working fine.

---

