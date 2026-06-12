---
title: "run xinput command after login?"
date: 2011-11-24
forum: General Help
---

### Post by ussndmac on 2011-11-24
Hi,

I have the following that works fine if I open a terminal window and type:

xinput set-prop "AlpsPS/2 ALPS GlidePoint" 121 0

it turns off the touch pad as expected.

I have tried putting it in .profile, touchpad still active after login.

I tried putting it in a file, setting the executable and adding it to System Settings > Startup Applications, touchpad still active after login.

Is there a log file that would have any info about what happened and if it did indeed run?

And what's the right way to get it to run after login?

This is in 11.04

Thanks,
Mac

---

### Post by matt_symes on 2011-11-24
Hi

Add it to the file /etc/rc.local file before the exit 0; command. You may have to set the DISPLAY environmental variable before calling it.

Kind regards

---

### Post by ussndmac on 2011-11-24
> **matt_symes said:**
> Hi

Add it to the file /etc/rc.local file before the exit 0; command. You may have to set the DISPLAY environmental variable before calling it.

Kind regards

Ah...doesn't rc.local run at boot?

I think I want this to run after login.

---

### Post by ptrakk on 2011-11-24
put it in your ~/.bash_profile file.

---

### Post by ussndmac on 2011-11-24
Doesn't seem to have any effect in rc.local or .bash_profile

---

### Post by matt_symes on 2011-11-24
Hi

> **ussndmac said:**
> Ah...doesn't rc.local run at boot?

I think I want this to run after login.

Yes it does so it looks like rc.local is not right for you.

Maybe exporting the display variable will help when added in the start up applications script.

```
DISPLAY=:0 xinput set-prop "AlpsPS/2 ALPS GlidePoint" 121 0
```

I take it 0 is your display.

Kind regards

---

