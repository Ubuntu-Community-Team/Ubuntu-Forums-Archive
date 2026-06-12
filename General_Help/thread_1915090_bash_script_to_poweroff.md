---
title: "bash script to poweroff"
date: 2012-01-25
forum: General Help
---

### Post by shibby4555 on 2012-01-25
Hey Ubuntuforums,
I've been experimenting around with writing some bash scripts. I'd like to have one to power off my computer when executed, how would I go about that?

I'd figure something like

gnome-terminal -x poweroff

but doesn't really work. Thanks!

---

### Post by wojox on 2012-01-25
To shutdown completely: 
```
sudo shutdown -h now
```

To reboot:
```
sudo shutdown -r now
```

---

### Post by drdos2006 on 2012-01-25
-h means to halt,  -r means to restart
regards

---

