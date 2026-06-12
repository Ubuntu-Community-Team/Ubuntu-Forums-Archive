---
title: "Automatically execute an script before shutting down"
date: 2011-12-24
forum: General Help
---

### Post by Josep CA on 2011-12-24
Hi,
I use Ubuntu 11.10 and I have a problem with LibreOffice. When I close it a process called soffice.bin remains active and I can't shut down Ubuntu until I kill it. I've tried reinstalling it but the problem remains. I would like to write a simple script to kill it and I'd like it to execute automatically when I close my machine or when I close LibreOffice so I'm able to shut down my machine automatically. Is it possible? I have some ideas about how I would write the script but I really don't know how to make it execute automatically. How would you do it? 

Cheers.

---

### Post by Lars Noodén on 2011-12-24
Some systems have /etc/rc.shutdown which corresponds to /etc/rc.local but executes on shutdown.  Unfortunately Ubuntu does not seem to have that.  So the solution would be to make a SystemV init script or an Upstart script and set it to kill the application upon shutdown.

There's a script template in /etc/init.d/skel but you can look at some of the other existing scripts to find one that is simpler and swap out the pieces you want.

---

### Post by Josep CA on 2011-12-24
Thanks I will try it and post the results!

---

