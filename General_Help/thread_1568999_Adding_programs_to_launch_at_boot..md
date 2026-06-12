---
title: "Adding programs to launch at boot."
date: 2010-09-06
forum: General Help
---

### Post by dek8 on 2010-09-06
I installed an application named Specto for monitoring websites and im trying to launch this on boot... i got XFCE4 and went into Application Autostart in the Session and Startup... and i cant seem to find out where to point Specto, is it in the /usr/share/applications or not cause i tried adding it from there and it wont launch on start... anyone got a rundown on this? trying to understand it but i just dont coming from windows. Not sure where applications are going at all and the file system is just a mess compared to windows so i have no control on what and where to look.... anyone?

Also Specto does not show up in task manager and in the Session tab of Sessions and Startup... why?

---

### Post by zvacet on 2010-09-06
Look in /usr/bin and see if app is there.

---

### Post by DemonBob on 2010-09-06
Try this in terminal. 

```
locate Specto
```

```
locate specto
```

---

### Post by dek8 on 2010-09-06
> **zvacet said:**
> Look in /usr/bin and see if app is there.

there is a python script to it there... that worked, the commands on the os are great, i gues it would be a nightmare cause its really a mess, alot to remember and alot to learn.

---

### Post by zvacet on 2010-09-06
> alot to remember and alot to learn.

Like every time you install new OS. ;)

---

