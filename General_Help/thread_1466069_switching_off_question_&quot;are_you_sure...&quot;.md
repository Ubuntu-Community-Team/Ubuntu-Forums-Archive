---
title: "switching off question &quot;are you sure...&quot; before shutdown"
date: 2010-04-30
forum: General Help
---

### Post by Screwdriver0815 on 2010-04-30
Hi,

I am thinking about installing Lucid right now but I have one question:

how do I switch off the question dialogue ("are you sure you want to end all programs and switch off?") which comes up when I want to shutdown the system?

is it the same way as it was in Karmic or is it different? If it is different: how do I do this?

thanks & regards
Steffen

---

### Post by dcstar on 2010-04-30
> **Screwdriver0815 said:**
> Hi,

I am thinking about installing Lucid right now but I have one question:

how do I switch off the question dialogue ("are you sure you want to end all programs and switch off?") which comes up when I want to shutdown the system?

is it the same way as it was in Karmic or is it different? If it is different: how do I do this?

thanks & regards
Steffen

Set this gconf key:

```
/apps/indicator-session/suppress_logout_restart_shutdown
```

---

### Post by Screwdriver0815 on 2010-05-01
> **dcstar said:**
> Set this gconf key:

```
/apps/indicator-session/suppress_logout_restart_shutdown
```

so it should be the same as in Karmic.

Thanks!

---

