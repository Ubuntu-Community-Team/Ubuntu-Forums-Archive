---
title: "Applications that run in the background"
date: 2009-10-18
forum: General Help
---

### Post by alan_uk on 2009-10-18
Can applications run in the background as they do in Windows? And if they do is there a way of knowing what they are as say as in a task manager. I can tell the more obvious ones as they are in the tool bars.

Thanks

Al

---

### Post by ikt on 2009-10-18
> **alan_uk said:**
> Can applications run in the background as they do in Windows? And if they do is there a way of knowing what they are as say as in a task manager. I can tell the more obvious ones as they are in the tool bars.

Thanks

Al

Yep

System > Admin > System Monitor > Processes will tell you all the programs running,

in terminal,

```
ps -e
```

will list all running processes as well, a terminal program similar to system monitor is called htop.

```
sudo apt-get install htop
```

```
htop
```

---

### Post by alan_uk on 2009-10-18
Thanks that helps

Al

---

