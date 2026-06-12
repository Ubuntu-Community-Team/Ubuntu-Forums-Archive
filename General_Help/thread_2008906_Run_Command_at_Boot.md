---
title: "Run Command at Boot"
date: 2012-06-23
forum: General Help
---

### Post by Slow Motion on 2012-06-23
I am trying to run this command at boot, before a user logs in.
```
nvidia-settings -a "[gpu:0]/GPUFanControlState=1" -a "[fan:0]/GPUCurrentFanSpeed=30"
```
How do I do this?

---

### Post by jocheem67 on 2012-06-23
Check out /etc/rc.local..

Put in a "sleep something &&" if necessary

Don't forget to 'chmod +x' it..

---

