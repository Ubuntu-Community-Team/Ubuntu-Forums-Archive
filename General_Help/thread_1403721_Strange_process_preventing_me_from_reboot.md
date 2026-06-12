---
title: "Strange process preventing me from reboot"
date: 2010-02-10
forum: General Help
---

### Post by pimseb on 2010-02-10
Hello,

When trying to reboot or shut down my ubuntu karmic system, I often see a warning telling me there is a process runing. This process is called "1000" and I really wonder what it is.
If someone has an idea ... ? 
I attach a screenshot of the popup window.
[ATTACH]146678[/ATTACH]
It's french but it asks if I still want to reboot because the program "1000" is not responding.
Thanks

---

### Post by doas777 on 2010-02-10
most likely it is a process with a pid of 1000, rather than a binary called "1000"

open a terminal and run top, and see if you have a proc with a pid of 1000

---

### Post by pimseb on 2010-02-10
I saw this windows 5 or 6 times. So why would it be always the pid number 1000 ? :)

---

### Post by doas777 on 2010-02-10
your right, most processes are ID'd at runtime with whatever number is next, but my supposition is that 1000 is a symbolic number and may refer to a special process. for instance the windows "system" process always has the same PID. I would not be surprised if linux had a simmilar set of special pids. just a thought.

---

