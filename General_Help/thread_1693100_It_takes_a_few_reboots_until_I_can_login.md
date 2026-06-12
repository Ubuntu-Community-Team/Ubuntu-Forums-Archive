---
title: "It takes a few reboots until I can login"
date: 2011-02-22
forum: General Help
---

### Post by ilcavero on 2011-02-22
A strange problem is bugging me, when I first boot my machine I get the login screen, I write my password and then the screen either goes black for a few seconds and returns again to an empty login screen, or the login box just goes gray and stuck. Either way I have to restart again and again the machine because once it fails to login it never works, but eventually after restarting I'm able to login and the rest of the system is fine.
I've checked the log file viewer looking for some error but I have found nothing, what can I do to figure out what is going on? I'm running 32-bit 10.04.

---

### Post by runeh76 on 2011-02-22
Hi

Try to reinstall GUI
Are u using gnome? If so:

```
sudo apt-get update
```

```
sudo apt-get install ubuntu-desktop
```

---

