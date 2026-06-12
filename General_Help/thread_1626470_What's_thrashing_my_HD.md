---
title: "What's thrashing my HD?"
date: 2010-11-20
forum: General Help
---

### Post by Rocket J Squirrel on 2010-11-20
ubuntu 10.10

At times something starts thrashing the HD. Often after the computer has been taken out of Suspension. The whole things slows down and stays slow. This can be fixed by logging off (which takes quite a while under this condition while the HD light stays on, solid) and logging back on. Then the system becomes responsive, with only HD light flickers. 

Anyway, I can't determine what process is doing the thrashing. System Monitor doesn't show any memory problems, and neither do top or htop. htop shows plenty of swap space available, and memory usage is on par with what it looks like when there is no thrashing.

Is there some tool that can display what processes are running the HD so hard?

---

### Post by Rocket J Squirrel on 2010-12-03
Anyone?

---

### Post by endotherm on 2010-12-03
I'd install and run iotop (with sudo) to see what process is running all the IO.

---

### Post by Rocket J Squirrel on 2010-12-03
Thanks, endotherm -- I'll see what it snoops out.

---

