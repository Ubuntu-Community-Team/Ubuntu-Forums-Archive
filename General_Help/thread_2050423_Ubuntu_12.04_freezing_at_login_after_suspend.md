---
title: "Ubuntu 12.04 freezing at login after suspend"
date: 2012-08-30
forum: General Help
---

### Post by maxim0512 on 2012-08-30
I have a fresh install of Ubuntu 12.04 Precise 64-bit on a custom-built desktop PC. Sometimes (with no discernible pattern), it hard freezes after displaying the login screen when waking up after being suspended.

Here's what I'm seeing in the tail of pm-suspend.log:

```
/etc/pm/sleep.d/10_unattended-upgrades-hibernate resume suspend: su
```

Note how it just cuts off halfway through the word "success."

To be explicit, by "hard freeze," I mean I can't switch to another virtual terminal or restart the X session. My only choice is to use the hardware power or reset button.

---

### Post by maxim0512 on 2012-08-31
Bump. Any ideas of things to try or places to look?

Thanks!

---

