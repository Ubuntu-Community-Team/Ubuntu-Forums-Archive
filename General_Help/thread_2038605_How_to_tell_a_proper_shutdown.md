---
title: "How to tell a proper shutdown?"
date: 2012-08-07
forum: General Help
---

### Post by Mr. Beekeeper on 2012-08-07
What is a definitive way to check and see if a computer shutdown properly?  Is there a log somewhere? 
I've read many replies of "Well, did it do a filesystem check on startup?"  That won't help me.  
My wake on lan has stopped working (over the local network), and it's the last thing I can narrow it down to.  I've reset the router, confirmed via WireShark that the packets were being sent, and sent the WOL from multiple devices too.  I have read a lot about the various problems that Ubuntu has had shutting down properly and seem to reach no consistent or definitive answer.  Any help would be greatly appreciated...getting up to turn on my server is...so...difficult....:lolflag:

---

### Post by Mr. Beekeeper on 2012-08-07
```
sudo halt now
```

Used to shut the system down properly and Wake on Lan worked for months and months.

After searching the man pages and reading online, I switched to using every permutation of "poweroff" and "shutdown", to no avail. In the past, I've confirmed that WOL does indeed work, and was reliable.  I've also confirmed that an improper shutdown makes it where the WOL doesn't work (power failure or hard-powering off the computer)..   

Is detecting a proper shutdown a system-specific thing?

---

### Post by Mr. Beekeeper on 2012-08-07
I guess my only solution is to switch distros to something else until Ubuntu gets back to being able to shut down more reliably.  Choice is the beauty of Linux!  (I could never do that on a Mac or Windows machine!)

---

