---
title: "Just a question there, about them processes."
date: 2010-02-01
forum: General Help
---

### Post by sicpsnake on 2010-02-01
Curious. Is it normal to have multiple processes of a program, say, Firefox? Because htop is displaying about 10-11 Firefox processes open, and about 11 mysqlds. Is this normal? Here's a screenshot.

---

### Post by squaregoldfish on 2010-02-01
Yes, it's entirely normal. Some programs will run ('fork') several different processes to perform separate tasks. MySQL, for example, will often start new processes as different people use the database.

You'll find that some process monitoring software will report different numbers of running processes, as they make different choices regarding how these extra forked processes are reported. On my machine, top reports 159 processes, while conky (another system monitor) reports 266!

Steve.

---

### Post by sicpsnake on 2010-02-01
Thank you for the answer.. I just wanted to make sure something wasn't messing up.

---

