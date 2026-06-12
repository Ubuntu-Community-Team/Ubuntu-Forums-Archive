---
title: "Adding multiple ssh keys to kwallet"
date: 2012-09-01
forum: General Help
---

### Post by FuturePilot on 2012-09-01
I have two ssh keys that I would like to have automatically unlocked when I log in. I have this script in ~/.kde/Autostart 
```
#!/bin/sh
export SSH_ASKPASS=/usr/bin/ksshaskpass
ssh-add </dev/null
```
This works perfectly for my first key (id_rsa) but I cannot get it to unlock a second key (id_rsa.2) I even manually added an entry in kwallet under ksshaskpass but it still doesn't unlock it. What am I missing?

---

### Post by FuturePilot on 2012-09-05
Bump

---

### Post by FuturePilot on 2012-09-06
Solved. I just simply added the path to both keys to the autostart script.

```
ssh-add /home/$USER/.ssh/id_rsa /home/$USER/.ssh/id_rsa.2</dev/null
```

---

