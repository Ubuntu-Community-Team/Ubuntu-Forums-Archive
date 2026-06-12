---
title: "Help with Upgrade to 10.04 (had to reboot)"
date: 2010-05-25
forum: General Help
---

### Post by jay3 on 2010-05-25
I have been running Ubuntu 9.10 for a while now. Today, I ran updates on my computer and also requested the upgrade to 10.04. Unfortunately, a few hours into it my computer hung. I had no choice but to reboot. When I did so the computer started a 10.04 screen and then went to a 'command line' for me to login. I am able to login, however, all i have is the 'command line'. What can i do now? Can I restart the upgrade from the 'command line'? Any assistance greatly appreciated. Thank you.

---

### Post by wilee-nilee on 2010-05-25
Try these two commands from the terminal.
```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

If no more installs are presented run.
```
sudo apt-get install ubuntu-desktop
```
or whatever desktop you want.

---

### Post by jay3 on 2010-05-25
> **wilee-nilee said:**
> Try these two commands from the terminal.
```
sudo dpkg --configure -a
```
 
```
sudo apt-get install -f
```
 
If no more installs are presented run.
```
sudo apt-get install ubuntu-desktop
```
or whatever desktop you want.
 
 
This helped!  thank you very much!

---

### Post by wilee-nilee on 2010-05-25
Put those two first commands on a cheat sheet they are invaluable, unless you can remember them. ;)

---

