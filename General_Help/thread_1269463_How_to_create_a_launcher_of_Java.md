---
title: "How to create a launcher of Java?"
date: 2009-09-18
forum: General Help
---

### Post by rocket16 on 2009-09-18
Hello all. I just installed Blue Java on my Ubuntu OS. To start it, I need to access the Directory bluej in my home folder, and type ./bluej. So, the commands in terminal are:
cd /home/username/bluej
./bluej
How do I unite these commands? I mean, how do I start bluej in a single command (that will access bluej directory and run bluej). I need this to create a custom launcher.

---

### Post by XCan on 2009-09-18
I think a script with ```
 sh -c "cd /home/username/bluej; ./bluej" 
``` should work.

---

### Post by rocket16 on 2009-09-18
Thansk! That works really!

---

### Post by rocket16 on 2009-09-18
Thanks again!

---

### Post by XCan on 2009-09-18
Glad to help, please consider marking thread as solved as well. :)

---

