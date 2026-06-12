---
title: "How to run a command (or script) at login"
date: 2012-04-11
forum: General Help
---

### Post by martyo on 2012-04-11
I've looked all over the forums for this I can't seems to figure it out. My monitor is a little bit washed out at startup and all that I want to do is to run the following at login:

```
xgamma -gamma 0.78 
```

I've tried putting it in startup applications and that doesn't work, and I've tried putting it in /etc/rc.local and that doesn't work either. Also, whenever I switch user accounts the gamma resets itself to 1.0, which makes me think that I need to find a way to run the command after login. Any suggestions?

---

### Post by kiirokurisu on 2012-04-11
Two possibilities you could try with putting it into Startup Applications:

[LIST=1]
[*]Use the full path to the executable (e.g. /usr/bin/xgamma)
[*]Put the command into a shell script, save that somewhere in your home directory and then add the shell script to Startup Applications (this option definitely works for me).
[/LIST]

---

### Post by Toz on 2012-04-11
If you are using lightdm as your DM, you can add:
```
session-setup-script=/usr/bin/xgamma -gamma 0.78
```
...to the end of **/etc/lightdm/lightdm.conf**

According to /usr/share/doc/lightdm/lightdm.conf, this will run that script on each session startup (login). 

I just tested this on my system and it worked. 

Note, you need to restart lightdm (or reboot) for it to take effect.

---

