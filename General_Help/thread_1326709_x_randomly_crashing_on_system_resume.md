---
title: "x randomly crashing on system resume"
date: 2009-11-14
forum: General Help
---

### Post by nerdy_kid on 2009-11-14
couldnt find any error messages...

---

### Post by nerdy_kid on 2009-11-14
found some errors; not very helpful.

```

2009-11-14 17:14:44   laptop    wpa_supplicant[542]    CTRL-EVENT-SCAN-RESULTS 
2009-11-14 17:14:44   laptop    acpid    client connected from 16002[0:0]
----> 2009-11-14 17:14:44   laptop    kdm[2171]    X server startup timeout, terminating
----> 2009-11-14 17:14:47   laptop    kdm[2171]    X server died during startup
----> 2009-11-14 17:14:47   laptop    kdm[2171]    Failed to start X server. Starting failsafe X server.
2009-11-14 17:14:52   laptop    acpid    client 16002[0:0] has disconnected
2009-11-14 17:14:52   laptop    acpid    client 16002[0:0] has disconnected

```

i found these digging though sys log, anywhere else i should look?  Ive looked in /var/log/Xorg.0.log; no errors.

---

### Post by ayampanggang on 2009-11-14
Same problem here.

Seems the hibernate/suspend feature is still really buggy, hit or miss feature in linux.

Last time on jaunty i have a 50/50 chance whether my system can go into suspend/hibernate. When it doesn't, it just stops there with a blank screen and a blinking cursor on the top left. And when it does, it got turned off properly, but will fail to resume 100% of the time.

I haven't bothered trying it in karmic except once, where the later case happens, where it can go into hibernate but fails to resume.

---

### Post by nerdy_kid on 2009-11-14
i think it depends on your hardware; mine has always worked fine until now.

---

### Post by nerdy_kid on 2009-11-14
i just discovered that my nvidia drivers are ancient...maybe updating them will help

---

