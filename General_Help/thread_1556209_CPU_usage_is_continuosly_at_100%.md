---
title: "CPU usage is continuosly at 100%?"
date: 2010-08-19
forum: General Help
---

### Post by mahela007 on 2010-08-19
HI.. My CPU usage on Ubuntu 10.04 frequently rises up to 100 % and stays there. What can I do to fix this?

---

### Post by Grenage on 2010-08-19
If you run 'top' from a terminal, what's using it?  You could also use System Monitor, under 'Administration'.

---

### Post by Rubi1200 on 2010-08-19
As Grenage already mentioned, you can check what is running and using up CPU and memory by using the ```
top 
```command in the terminal.

You might also want to check if Compiz is running and turn it off to see if that produces any change.

---

### Post by mahela007 on 2010-08-19
I tried 
top
It said something like 'apt-update'was running at 40% CPU usage.

---

### Post by Grenage on 2010-08-19
That's possible, if it's updating, what about the other 60%?

Tip: You can press *c* to order by CPU use.

---

