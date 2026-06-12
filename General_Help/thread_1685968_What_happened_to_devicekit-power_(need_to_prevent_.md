---
title: "What happened to devicekit-power? (need to prevent users from suspending/hybernating)"
date: 2011-02-11
forum: General Help
---

### Post by msp3k on 2011-02-11
Hello gurus,

I am in the midst of planning a much-needed upgrade of our workstations from 9.10.  Playing around with the daily natty build, I have noticed that there is no devicekit-power package anymore.  I rely on tweaks to the /usr/share/polkit-1/actions/org.freedesktop.devicekit.power.policy file to prevent users from being able to suspend or hybernate their workstations.

What has replaced devicekit, and are there any updated instructions for how to prevent users from hybernating/syspending?

---

### Post by msp3k on 2011-02-11
SOLVED: devicekit-power -> upower

The new file to edit is:
/usr/share/polkit-1/actions/org.freedesktop.upower.policy

---

