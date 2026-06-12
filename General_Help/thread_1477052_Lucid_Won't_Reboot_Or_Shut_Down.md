---
title: "Lucid Won't Reboot Or Shut Down"
date: 2010-05-08
forum: General Help
---

### Post by omgseth on 2010-05-08
Just installed Lucid Lynx and when I click Restart or Shut Down it just takes me to the login screen. If I try to click Restart or Shut Down from the login screen, nothing happens :\

---

### Post by TheNerdAL on 2010-05-08
> **nitstorm said:**
> ubuntuforums.orgubuntuforums.org/newreply.php
Tried the command line for that?

for shutting down instantly:
```

sudo shutdown -P now
(or)
sudo poweroff

```

and for restart
```

sudo reboot

```
Some people have that problem. I don't think there is a fix but you can do what nitstorm said.


EDIT: Or you can try this: 

> **dino99 said:**
> some users have found a permanent tweak:

sudo gedit /etc/default/grub

change : GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"

by : GRUB_CMDLINE_LINUX_DEFAULT="quiet acpi=force"

may not work for everyone

There is a bug report here if you want to support the fix: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/552316](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/552316)

---

### Post by omgseth on 2010-05-08
I was able to use the sudo reboot, as for the acpi=force thing, it didn't work ( thanks for helping though! ). New thing though, after the reboot, I have no sound!
D:

---

### Post by TheNerdAL on 2010-05-08
> **omgseth said:**
> I was able to use the sudo reboot, as for the acpi=force thing, it didn't work ( thanks for helping though! ). New thing though, after the reboot, I have no sound!
D:

This thread might be of use: [http://ubuntuforums.org/showthread.php?t=1438224](http://ubuntuforums.org/showthread.php?t=1438224)

---

