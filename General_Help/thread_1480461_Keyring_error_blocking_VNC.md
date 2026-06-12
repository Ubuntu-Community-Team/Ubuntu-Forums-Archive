---
title: "Keyring error blocking VNC?"
date: 2010-05-11
forum: General Help
---

### Post by Redundant Username on 2010-05-11
I'm trying to use VNC on my headless desktop server that's running lucid, but I can only use SSH because a pop asking me to unlock the keyring shows up every time I try to use VNC. I don't have a monitor for that desktop, so I was wondering, is there any way to remove the keyring/to automatically unlock it during autologin? I don't remember what a site I found it on, but I used this to remove my keyring yesterday. It's no longer working today. ```
rm ~/.gnome2/keyrings/login.keyring
```

---

### Post by Redundant Username on 2010-05-11
*legal bump*

---

### Post by cbraxton on 2010-05-11
It's a bug. See:

  [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/562423](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/562423)

There is a workaround in reply #11 in the thread. (Base64 encoding
of the password that is mentioned therein can be done with the "base64"
command, see "man base64" for details.)

---

### Post by Redundant Username on 2010-05-12
Would this be possible to do with a Windows SSH client?

---

### Post by Redundant Username on 2010-05-12
*legal bump* I can't log onto SSH for some reason, but FTP works. I'll just have to move everything over there.edit fixed

---

