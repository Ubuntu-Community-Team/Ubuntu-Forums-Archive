---
title: "Connect to Windows machine"
date: 2010-12-29
forum: General Help
---

### Post by medeiom on 2010-12-29
I'm using Ubuntu for the first time and love it!! It sees my network name and my XP machine name. But it fails to connect due to "Unable to Mount Failed to retrieve share list from server" error msg.

Any feedback would be much appreciated!

---

### Post by cariboo on 2010-12-29
Have you got shares set up properly on your Windows system? Open a terminal on your ubuntu system, and type:

```
smbtree
```

It will show you a list of all the shares that are available.

---

### Post by medeiom on 2010-12-30
smbtree showed me a list of shared folders from my XP machine.  It appears that a reboot was all I needed from my Ubuntu machine.  I am now able to communicate with each shared folder.

Ubuntu rocks! and thanks for the reply.

---

