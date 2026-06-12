---
title: "what?? This program must be run as root when no X server is active"
date: 2011-08-16
forum: General Help
---

### Post by bboques on 2011-08-16
What does this mean?

bit@Bit:~$ aticonfig --odgc --adapter=all
aticonfig: This program must be run as root when no X server is active


I just bought a new computer, had a computer shop make it, and went  through all the steps but I can't tell what number my GPUs are.  I am  mining successfully on my CPU so it works, but why won't my cards show  up?

---

### Post by oldos2er on 2011-08-16
It means you need to run it with "sudo" ```
sudo aticonfig --odgc --adapter=all
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by WorMzy on 2011-08-16
You also need to kill off X, and run it from a tty.

```
sudo service gdm stop
```

---

