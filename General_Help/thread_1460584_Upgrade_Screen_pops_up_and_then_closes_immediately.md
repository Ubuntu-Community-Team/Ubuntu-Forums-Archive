---
title: "Upgrade Screen pops up and then closes immediately"
date: 2010-04-23
forum: General Help
---

### Post by seamles on 2010-04-23
Hi,

I can't seem to upgrade or run any core ubuntu processes. When I try to open something (such as upgrade or ubuntu tweak), the screen will pop up and then close immediately. I restarted my computer a couple times but I'm not sure what else I can do. 

Any help is great

Thanks

---

### Post by jmszr on 2010-04-23
seamles,

I'm not sure, but it seems similar to a problem I had where the update manager and synaptic etc. would close immediately after opening.

The fix was:

```
sudo rm /var/cache/apt/*.bin
```

Hope that helps.

---

### Post by seamles on 2010-04-23
Well that seemed to do the trick. THANKS!

---

