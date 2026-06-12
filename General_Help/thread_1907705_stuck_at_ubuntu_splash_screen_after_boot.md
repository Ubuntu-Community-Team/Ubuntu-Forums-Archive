---
title: "stuck at ubuntu splash screen after boot"
date: 2012-01-11
forum: General Help
---

### Post by kenneth.koontz on 2012-01-11
After boot, Ubuntu will not get past the splash screen right before login. I opened a console, ctrl-alt-f1, logged in and checked the logs. Nothing relevant pops out. I stopped the lightdm service by running the following.

```

sudo service lightdm stop

```

After stopping the service, I then ran startx. Which started up a session.

Any suggestions on how to get my system booting to login normally?

---

### Post by raja.genupula on 2012-01-12
whats the case after restarting your PC , are you getting the same problem again ?

---

### Post by kenneth.koontz on 2012-01-12
After rebooting no luck.

---

### Post by raja.genupula on 2012-01-12
I think it might be issue of your graphic drivers , are you able to recovery mode from grub menu ? If so choose that and then boot to failsafeX mode and reinstall your graphics driver .

All the best.

---

