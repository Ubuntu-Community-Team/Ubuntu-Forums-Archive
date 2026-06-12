---
title: "Cannot uninstall with Wubi"
date: 2011-09-22
forum: General Help
---

### Post by gbchaosmaster on 2011-09-22
I botched my Ubuntu install (it was a dual-boot installed with Wubi) and now it only boots right into a GNU GRUB terminal. I figured it was beyond repair and I'd uninstall/reinstall. However, when I try to uninstall with Wubi, it says "C:/ubuntu/disks is corrupt and unreadable" and fails. How can I remove the corrupt system so that I can put a fresh install on?

---

### Post by Frogs Hair on 2011-09-22
See the uninstall section , you can remove it manually from Computer / Program files . Delete the wubildr folder and the Ubuntu program folder from C programs . 

Running disk clean-up  and defrag is a good idea before trying again . [https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

---

### Post by gbchaosmaster on 2011-09-22
The disks folder in C:/ubuntu cannot be deleted. When I try to remove it, it gives the error "Cannot delete disks: The file or directory is corrupted and unreadable."

---

### Post by Frogs Hair on 2011-09-22
I would see this thread because my suggestion was from the Wubi guide and I remember this problem coming up before .  
  

[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

