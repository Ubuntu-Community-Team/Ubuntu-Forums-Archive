---
title: "Accessing .bashrc Variables From Cron Job"
date: 2009-11-22
forum: General Help
---

### Post by Cerin on 2009-11-22
I have a script run by cron, and the script tries to access environment variables defined in my .bashrc file. When I run the script myself, it can access the variables just fine, but when cron runs it, I get an error saying the variables aren't defined.

How do you ensure cron loads your .bashrc file before it runs your script?

---

### Post by KiLaHuRtZ on 2009-11-22
Why not just define the environment variables right in you script?

---

### Post by Cerin on 2009-11-22
I try and follow the "don't repeat yourself" principle. I have several scripts that use these variables, so it's easier to put them in one file, and reference that one file, than duplicate the variables in dozens of scripts.

---

