---
title: "Synaptic Manager won't open help"
date: 2011-06-02
forum: General Help
---

### Post by SVEN1 on 2011-06-02
Did an update today by update manager. Noticed Virtualbox problems, will no longer start XP when program is opened. Tried uninstalling and reinstalling VB 4.0.8 would not work .

Now I have a problem with Synaptic Package Managar. It will not open an error message pops up. How do I fix this??
Thanks

---

### Post by LowSky on 2011-06-02
Have you tried running the commands it telling you to run... 

HINT:

```
sudo '/etc/init.d/vboxdrv setup'
sudo dpkg --configure -a
```

---

### Post by SVEN1 on 2011-06-03
Thanks, fixed both problems in less than 5 minutes using the terminal, completely forgot what I did..... I was  rushing as I had to get out the door to  catch the bus.
All is good again.

---

