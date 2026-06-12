---
title: "How to add a password to a terminal script"
date: 2009-12-11
forum: General Help
---

### Post by ldclan on 2009-12-11
I have a terminal command to copy a specific folder from 1 hard drive to a second hard drive as a backup. Also I'm using Schedule Tasks to start the terminal at a given time. The problem I'm having is, it is prompting me for my password. Is there a way to add my password to the terminal command so it will not ask for one? Below is my script for the terminal command:

"sudo cp -dpRuvx /media/NAS_Disk-2/GRAPHICS-NAS /media/NAS_Disk-3"

Any help would be greatful, thank you.

---

### Post by crolanx on 2009-12-11
Try
```
echo <your password> | sudo -S cp -dpRuvx /media/NAS_Disk-2/GRAPHICS-NAS /media/NAS_Disk-3
```

But please remember that this could be a security risk.

---

