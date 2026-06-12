---
title: "how to create a new file in  modprobe.d"
date: 2010-07-12
forum: General Help
---

### Post by ubunguy on 2010-07-12
i was using ubuntu then switched to pclinux (since its based on ubuntu i thought id post my question here)
 
i just want to create a file in dolphin to save in modeprobe.d
 
but when i open dolphin it does not give me that option to save as or create new?
 
 
do i have to log on as root or something to get privliges let me know i just want to create a file and save and edit in modeprobe.dl
 
thanks

---

### Post by CannibalZerg on 2010-07-13
Open terminal, than run:
```
sudo touch /etc/modprobe.d/my_file
gksu gedit /etc/modprobe.d/my_file

```First command creates empty file, second - opens it in editor with root privilege.

---

### Post by Yellow Pasque on 2010-07-13
You probably need root permissions to create a file there.. ;)

---

