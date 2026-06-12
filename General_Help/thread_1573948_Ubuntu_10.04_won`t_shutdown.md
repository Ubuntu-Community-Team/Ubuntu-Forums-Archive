---
title: "Ubuntu 10.04 won`t shutdown"
date: 2010-09-13
forum: General Help
---

### Post by s.v.z on 2010-09-13
Hi everyone! I`ve got an hp6735b laptop with Ubuntu 10.04 (2.6.32-24-generic) installed. Recently I`ve discovered that when I do ```
sudo shutdown +m
``` the system won`t. It begins to shutdown, shows some messages about services being stopped, than shows the splash screen.. and that`s all. The splash screen stays there forever. If I press the power button and select the shutdown option, the system shuts down nicely. Is there a way to fix it?

---

### Post by TeoBigusGeekus on 2010-09-13
Try 
```
sudo shutdown -h now
```

---

### Post by s.v.z on 2010-09-13
This one works, as well as the ```
sudo shutdown -h +m
``` So is the problem in "-h" missing?

---

### Post by TeoBigusGeekus on 2010-09-13
The -h option in the shutdown command is for the system to power off after shutdown.
For more info
```
man shutdown
```

---

### Post by s.v.z on 2010-09-13
Thanks a lot.

---

### Post by TeoBigusGeekus on 2010-09-13
You're welcome.

---

