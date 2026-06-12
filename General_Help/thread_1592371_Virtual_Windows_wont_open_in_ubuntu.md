---
title: "Virtual Windows wont open in ubuntu"
date: 2010-10-10
forum: General Help
---

### Post by dvo_photo on 2010-10-10
Hi I get an error message 
Failed to start virtual machine XP
Result Code: NS_error _failure (0x80004005)
Component: Console
Interface: IConsole {6375231a-c17c-464b-92cb-ae93128d71c3} 

I really need to get into my photoshop :(

Thanking you in advance for your help:smile:
Diana

---

### Post by sikander3786 on 2010-10-10
I think you need to recompile the Virtualbox kernel modules. First make sure that the package dkms is installed. Then from terminal,

```
sudo /etc/init.d/vboxdrv setup
```

---

