---
title: "Remove icons from dashboard in ubuntu 11.10"
date: 2011-12-01
forum: General Help
---

### Post by guyver_dio on 2011-12-01
Hi

I recently installed the crossover demo and have now tried uninstalling it. I think I've uninstalled it successfully but the launch icons remain in the applications section of the dashboard.

Is there any 1 directory where these icons reside so that I could simply just delete them or is it a little more complex then that?

Any help would be appreciated.

---

### Post by raja.genupula on 2011-12-01
if you wanna remove an application completely including with its configuration files then do purge

```
sudo apt-get remove --purge <App_name>
```

---

### Post by dfarrell07 on 2012-02-15
I think you can selectively remove icons from the Unity bar graphically. Something like right click -> unpin. I'm running GNOME3, so I can't test it to be sure.

---

