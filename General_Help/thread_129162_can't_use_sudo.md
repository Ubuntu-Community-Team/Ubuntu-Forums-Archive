---
title: "can't use sudo"
date: 2006-02-13
forum: General Help
---

### Post by tanari on 2006-02-13
I have strange bug, everytime when I use sudo, I get this:
 
```

tanari@ubuntu:~/apps/gnomebaker-0.5.1$ sudo make uninstall
sudo: /etc/sudoers is owned by uid 1000, should be 0
tanari@ubuntu:~/apps/gnomebaker-0.5.1$

```

Now I can't use synaptic, install or uninstall apps :(

---

### Post by heimo on 2006-02-13
Boot to recovery mode and change ownership of /etc/sudoers to root.

Probably something like this should work:
```
chown root:root /etc/sudoers
chmod 0440 /etc/sudoers

```

---

