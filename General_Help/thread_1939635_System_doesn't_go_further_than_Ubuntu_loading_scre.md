---
title: "System doesn't go further than Ubuntu loading screen"
date: 2012-03-12
forum: General Help
---

### Post by Tornikee on 2012-03-12
To put it simply: yesterday I set 'use current desktop wallpaper as login screen background' in Ubuntu Tweak, and then uninstalled LightDM Manager, as I thought the only thing it did was allow me to change login screen backgrounds. After a restart, the system doesn't go past Ubuntu loading screen (the loading animation goes on infinitely).

I'm almost 100% sure the issue is down to the uninstalling of LightDM, but how can I solve it? Will booting via Ubuntu Live CD and installing the application solve it?

---

### Post by mac666 on 2012-03-12
start in recovery mode, and go to shell and install it.
no live cd req.

---

### Post by Tornikee on 2012-03-12
> **mac666 said:**
> start in recovery mode, and go to shell and install it.
no live cd req.
Thanks for the reply. I think I tried recovery mode last night and it still couldn't reach any further than loading screen. Will try again. Could you post in  a bit more detail how I can install LightDM from recovery mode?

---

### Post by Basher101 on 2012-03-12
once you are in recovery you should get some kind of option to open a terminal or use commands (not 100% sure what you have to do there since i never had to use it..) anyways, once you can type a command use > sudo apt-get install LightDM

That is **_IF_** LightDM is the correct package name for the manager. I could tell you in a few minutes the exact package name from synaptic when i rebooted into ubuntu (using windows atm)

---

### Post by Tornikee on 2012-03-12
> **Basher101 said:**
> once you are in recovery you should get some kind of option to open a terminal or use commands (not 100% sure what you have to do there since i never had to use it..) anyways, once you can type a command use 

That is **_IF_** LightDM is the correct package name for the manager. I could tell you in a few minutes the exact package name from synaptic when i rebooted into ubuntu (using windows atm)
Thank you. Will try that later today.

---

### Post by HavarN on 2012-03-12
If the problem continues, you could try replacing lightdm with gdm or kdm.```
sudo apt-get install gdm
```

---

### Post by Tornikee on 2012-03-12
I can't get into recovery mode - after selecting it, the screen goes blank, and Ctrl+Shift+Del brings it to Ubuntu loading screen. Is there anything I can do from Live CD?

---

### Post by 2F4U on 2012-03-12
Are you able to get to a console (Ctrl-Alt-F1,F2,...) when the machine hangs?

---

