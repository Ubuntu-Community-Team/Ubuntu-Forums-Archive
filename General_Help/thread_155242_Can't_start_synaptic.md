---
title: "Can't start synaptic"
date: 2006-04-04
forum: General Help
---

### Post by BrownieMan on 2006-04-04
I can't start synaptic. I orginialy got an error message; 

"sudo: /etc/sudoers is owned by uid 1000, should be 0"

 but I fixed that with

chown root:root /etc/sudoers
chmod 0440 /etc/sudoers

but I still can't get into synaptic.

---

### Post by aysiu on 2006-04-05
So you did [this](http://ubuntuforums.org/showthread.php?t=86412) and it worked?

What happens when you type this in the terminal? What's the output? ```
gksudo synaptic
```

---

### Post by BrownieMan on 2006-04-05
I reinstalled the OS, I think the problem had to do with some permissions I messed around with in /etc (inclusive)

---

