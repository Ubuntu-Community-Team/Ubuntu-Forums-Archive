---
title: "Automatically change default in GRUB2"
date: 2010-12-15
forum: General Help
---

### Post by Zeophlite on 2010-12-15
So I have Windows 7 and Ubuntu dual booted on my computer, and the default is Ubuntu.  I was wondering if it was possible to make it such that the default is the last booted system?  As in, if I was in Windows, and restarted, then GRUB would highlight Windows.

The main motivation is to for when the computer restarts automatically (say after an update).  I may not be around during the 10 seconds before it boots into Ubuntu.

---

### Post by NCLI on 2010-12-15
Press alt+F2, then enter: ```
gksudo nano /etc/default/grub
```
Find this line(The number may not be a 0):```
GRUB_DEFAULT=0
```

Now delete the 0 and type "saved". It should now look like this:
```
GRUB_DEFAULT=saved
```

Close the editor, and say yes when it asks whether you want to save the changes.

Now open a terminal, then run this command:
```
sudo update-grub
```

It should now boot the last used OS when you reboot :KS

---

