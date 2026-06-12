---
title: "How can I Disable Hibernation?"
date: 2011-01-01
forum: General Help
---

### Post by ellalan on 2011-01-01
I get my window get locked and have to enter password when I leave unattended for a while, how can I disable it please. Ubuntu 10.04.

---

### Post by Frogs Hair on 2011-01-01
To disable lock screen go to preferences > screensaver and remove the check from the lock screen when inactive option . From the power settings tab you can disable sleep. Not sure if this is what your after.

---

### Post by ellalan on 2011-01-01
Thanks a lot for the speedy response.

---

### Post by flomar on 2011-01-19
The title is misleading. 

I am really looking for a way to disable hibernation. I installed via Wubi and don't want to unintentionally press the hibernate button.

This option doesn't work anymore in 10.10
> In gconf-editor disable the keys by unchecking :
/apps/gnome-power-manager/can_hibernate 
Right click on these keys and set as mandatory

---

### Post by exXplode on 2011-02-26
> **flomar said:**
> The title is misleading. 

I am really looking for a way to disable hibernation.

Hi! I found out, how to do it. You have to tell PolicyKit to forbid hibernation (in this example for all user groups):

```
cat << EOF | sudo tee /etc/polkit-1/localauthority/50-local.d/02-disable-hibernation.pkla
  [Disable hibernate/suspend for all groups]
  Identity=unix-group:*
  Action=org.freedesktop.upower.hibernate
  ResultActive=no
  ResultInactive=no
  ResultAny=no
EOF
```

I found the hint here: [https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/621416/comments/5](https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/621416/comments/5)

---

