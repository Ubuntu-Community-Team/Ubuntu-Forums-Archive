---
title: "How to manually start lightdm"
date: 2011-10-31
forum: General Help
---

### Post by xr4ti on 2011-10-31
Newbie here...
 
I installed lightdm and xfce4 on my 11.10 64-bit server. Now lightdm automatically loads when I start my computer. How can I stop this? I want to login to a shell and then start my desktop environment if needed.
 
Please help.

---

### Post by collisionystm on 2011-10-31
Easy

Just disable the display manager by renaming the config file that chooses it

Open Terminal

```
sudo mv /etc/X11/default-display-manager default-display-manager.old
```

reboot

---

### Post by ajgreeny on 2011-10-31
I don't think it is essential to have a display manager at all, if you don't want one;  you can start the DE with command startx.

Perhaps xfce4 has lightdm as a dependency now;  I don't know about that.

---

