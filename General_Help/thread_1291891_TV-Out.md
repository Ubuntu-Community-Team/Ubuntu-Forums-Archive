---
title: "TV-Out"
date: 2009-10-15
forum: General Help
---

### Post by oospill on 2009-10-15
hello.. I've got a laptop running Ubuntu Desktop.  my laptop has an S-Video out.. I just figured out that it's gonna take more than the right cable to get tv-out.  anyone have any ideas?

thanks,
oospill

---

### Post by earthpigg on 2009-10-15
what video drivers are you using?

if nvidia, plug it in and try running 'sudo nvidia-settings' and see if the TV is simply regarded by your system as another display.

---

### Post by oospill on 2009-10-15
arg.  yes I'm running with NVidia .. into a wall.  I tried that, but dono where to look.

---

### Post by earthpigg on 2009-10-15
```
sudo nvidia-settings
```

and then hunt around for the 'detect displays' button?

---

