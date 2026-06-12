---
title: "Time problem in dual boot"
date: 2011-04-18
forum: General Help
---

### Post by ptcat60 on 2011-04-18
When I switch from ubuntu to windows the computer clock appears to be set to GMT rather than my time zone, windows only updates the time once a month, is there a solution for this? 

Thanks in advance

Ptcat

---

### Post by matt_symes on 2011-04-18
Hi

> **ptcat60 said:**
> When I switch from ubuntu to windows the computer clock appears to be set to GMT rather than my time zone, windows only updates the time once a month, is there a solution for this? 

Thanks in advance

Ptcat

Windows uses local time and Ubuntu uses GMT by default. The easiest way is to change Ubuntu so it uses local time.

Open a terminal and type

```
sudo nano /etc/default/rcS
```

Make sure this is in there

```
UTC=no
```

Kind regards

---

