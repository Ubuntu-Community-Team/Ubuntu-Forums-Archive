---
title: "Uninstalling cairo-dock lead to loss of everything!"
date: 2009-10-16
forum: General Help
---

### Post by ablom on 2009-10-16
I encountered quite a few bugs when I upgraded to cairo-dock 2.1, so I decided to remove it and reinstall it. However, when I did remove it, it must've taken a bunch of other programs with it. Now, when I boot all I get is a blank screen. The only program I removed was cairo-dock and it's dependencies, yet everything is gone. Has anyone else experienced this? Is there anything I can do about it?

---

### Post by DeMus on 2009-10-16
> **ablom said:**
> I encountered quite a few bugs when I upgraded to cairo-dock 2.1, so I decided to remove it and reinstall it. However, when I did remove it, it must've taken a bunch of other programs with it. Now, when I boot all I get is a blank screen. The only program I removed was cairo-dock and it's dependencies, yet everything is gone. Has anyone else experienced this? Is there anything I can do about it?

Install it again to get the dependencies back. Then when un-installing again look carefully which dependencies will be un-installed also and in doubt, don't un-install.

---

### Post by ablom on 2009-10-16
How do I know what to reinstall in recovery mode?

---

### Post by DeMus on 2009-10-16
> **ablom said:**
> How do I know what to reinstall in recovery mode?

When you are at the command line type:
```
sudo apt-get install cairo-dock
```
You will be asked for your password since it is a sudo operation.

---

### Post by ablom on 2009-10-16
I tried it and got nothing. It seems to have removed all programs but is not bringing them back.

---

### Post by ablom on 2009-10-16
Bump

---

### Post by ablom on 2009-10-16
Bump

---

### Post by theZoid on 2009-10-17
try

```
sudo apt-get install -f
```

to install missing dependencies

---

