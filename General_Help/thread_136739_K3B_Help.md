---
title: "K3B Help"
date: 2006-02-26
forum: General Help
---

### Post by Jeffery Mewtamer on 2006-02-26
I'm trying to burn an iso using K3B. It starts burning, but about 11 seconds after starting returns this message:

CDrecorder does not have permission to open the drive. This can be fixed using K3B setup.

or something along those lines. I've run K3B setup and it hasn't helped. Can anyone provide a solution to this problem?

---

### Post by FlakJacket on 2006-02-26
usually if you run K3B setup when you first turn it on it will give root priv's to your drive.  If not you could always do alt+f2 and 
```
 kdesu k3b 
``` and just burn it as root

Hope that helps,
 Flak

---

### Post by Jucato on 2006-02-26
or ```
sudo chmod +s /usr/bin/cdrdao
```

---

