---
title: "Alt+Left/Right now switches ttys..."
date: 2009-12-11
forum: General Help
---

### Post by stderr on 2009-12-11
As of 20 minutes ago, Alt + Left/Right switches ttys - left moves down one, right moves up one. This occurs no matter which application has focus - e.g., in Firefox, Alt+Left will normally move back one page in the history, but now it switches me to tty6. 

This is on a 9.10 system I reboot irregularly; uptime is currently 18 days, and I haven't installed any updates for days/weeks. I can't identify any changes beforehand that could have caused it. System->Preferences->KeyboardShortcuts doesn't have any mappings for Alt+Left or Alt+Right, and the change workspace mappings are still set to Ct+Al+L,Ct+Al+R and work OK. 

This is running Metacity with binary NVIDIA + Xinerama (no TwinView). 

NB: I'm moreorless expecting things to return to normal following a reboot, but can't afford to do so just yet, so any workarounds would be appreciated :)

---

### Post by falconindy on 2009-12-11
Strange. This is normal behavior outside of an X session. Rather than rebooting, try restarting X? Failing that, drop down to init 1 and back to 5 (recreating the tty's in the process).

---

### Post by stderr on 2009-12-12
> **falconindy said:**
> This is normal behavior outside of an X session.


Ah, I didn't realise: that makes more sense now. Thanks falconindy, I'll try restarting X.

---

