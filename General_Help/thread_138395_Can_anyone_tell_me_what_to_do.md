---
title: "Can anyone tell me what to do?"
date: 2006-03-01
forum: General Help
---

### Post by lesada411 on 2006-03-01
What must I do when I click on to update and a window appears that says."Unable to get exclusive lock"  Another package management application (like apt-get or aptitude) already running. Please close that application.  How do I close the application?  Thank-you.

---

### Post by evilghost on 2006-03-01
Close Synaptic if you have it open.

---

### Post by lesada411 on 2006-03-01
Thank-you but there`s nothing else running on the desktop.  Can it be something else?

---

### Post by aysiu on 2006-03-01
```
sudo killall synaptic
sudo killall apt-get
sudo killall dpkg
```

---

