---
title: "I have to restart networking when the power goes out"
date: 2011-10-30
forum: General Help
---

### Post by tbharber on 2011-10-30
I have a Ubuntu server running 11.04.  The system works perfectly except for when the power goes out.  When the power goes out/back on the computer, modem/router will restart but the problem is because the Ubuntu box reboots faster than the router/modem, it does not start networking upon boot like normal.  When this happens I have to login and run a "sudo /etc/init.d/networking restart" to get it working.  

Does anyone have a solution so if my router is not up upon boot Ubuntu will do this itself when the router does come back online?

Thanks!!!!

---

### Post by mike555 on 2011-10-30
UPS battery backup

---

### Post by tbharber on 2011-10-30
Haha I was thinking that too but I'm more so looking for a solution to run on the box so it would detect if networking is not running and start it automatically.  

Any thoughts?

---

### Post by dcstar on 2011-10-31
> **tbharber said:**
> Haha I was thinking that too but I'm more so looking for a solution to run on the box so it would detect if networking is not running and start it automatically.  

Any thoughts?

[http://ubuntuforums.org/showthread.php?t=1290269](http://ubuntuforums.org/showthread.php?t=1290269)

---

