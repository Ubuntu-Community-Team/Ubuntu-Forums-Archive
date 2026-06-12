---
title: "GSM Upstart Job"
date: 2011-03-21
forum: General Help
---

### Post by blink-182 on 2011-03-21
Hello,

I wanted to install the new NVIDIA Driver. Therefore I wanted to stop the Xserver. Unfortunatelly I typed sudo /etc/init.d/gdm dtop instead of "stop". Now gdm appears to be an "Upstart Job" and i can't kill the Xserver, nor stop gdm.

Can you help me?

Thank you very much!

EDIT:

Sry I ment "GDM Upsart Job" having a little trubble with my wireless keyboard...

---

### Post by tredegar on 2011-03-21
System - Administration - Hardware Drivers should do it all for you.

If you are determined to do it manually then **sudo service gdm stop** is probably what you need.

---

### Post by oooh on 2011-04-04
```
sudo service gdm stop
stop: Unknown instance:
```

never worked for me

---

