---
title: "Printer Stopped Printing"
date: 2011-01-12
forum: General Help
---

### Post by BigYellowDog on 2011-01-12
My print queue has stopped printing, since the printer was turned off then I printed a document.  I've tried to restart printing but nothing.  

```

sudo cupsenable HP_LaserJet_P1005
sudo lpadmin -E -p HP_LaserJet_P1005
sudo service cups restart
```

The queue status is 
```
HP_LaserJet_P1005 is ready and printing
```

---

### Post by BigYellowDog on 2011-01-13
What I found out is, if my printer is turned off when a job is submitted, the printer refuses to print anything after it is turned back on.  cups submits jobs to the printer, and everything appears to work, there's just no output.  Restarting cupsd or removing the queue has no effect.  The only solution is to plug the printer into a Windows box and print something, this resets the printer in some way.

---

