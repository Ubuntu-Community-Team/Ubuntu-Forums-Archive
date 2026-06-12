---
title: "Update manager won't go away"
date: 2009-09-14
forum: General Help
---

### Post by lumix on 2009-09-14
Beside the fact that this unruly application installs kernel upgrades that crash (with a panic) and can't find it's own .deb files, *I can't make it sit, stay, and fetch on command.*

Lo, for I have disabled "check for updates" in its foul belly, but the beast doth have its own bidding none-the-less.

---

### Post by bobince on 2009-09-14
Use synaptic to remove update-manager/update-notifier?

---

### Post by epicoder on 2009-09-14
Removing it might be dangerous... I would recommend adding this command to your startup apps. The reason it still starts is because it will **always** check for updates on login, and if there are any, it will start.

```
gksudo apt-get update ; gksudo apt-get upgrade
```

Doing this means you will have to enter your password upon login, but Update Manager will have no updates to trigger it.

---

### Post by drs305 on 2009-09-14
> **lumix said:**
> Beside the fact that this unruly application installs kernel upgrades that crash (with a panic) and can't find it's own .deb files, *I can't make it sit, stay, and fetch on command.*

Lo, for I have disabled "check for updates" in its foul belly, but the beast doth have its own bidding none-the-less.

If you provide more details perhaps we can help tame the beast for you.

Note: apt-get is a terminal command, so "sudo" should be used, with "gksudo" reserved for graphical apps such as nautilus and gedit.

---

### Post by epicoder on 2009-09-14
sudo will not work in this case, because the startup apps are run in the background. Therefore there will be no terminal to type the password in. However, gksudo creates a window to type the password in.

---

### Post by drs305 on 2009-09-14
> **sh228 said:**
> sudo will not work in this case, because the startup apps are run in the background. Therefore there will be no terminal to type the password in. However, gksudo creates a window to type the password in.

Missed the 'startup' part ... nice way to get to the authentication!

---

