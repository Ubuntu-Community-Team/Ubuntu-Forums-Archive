---
title: "Editing Dual Boot Startup"
date: 2010-09-03
forum: General Help
---

### Post by David Vincent-Jones on 2010-09-03
Ubuntu 10.04

I am dual-booting along with Windows.

I need to change the order of boot options so that Windows is the automatic selection rather than Ubuntu.

I cannot find the file to make the change and not sure what changes I should make when I do find it .

Help would be appreciated.

---

### Post by garvinrick4 on 2010-09-03
Install startupmanager and you can change from GUI. Open start up manager and it will be self explanitory.

```
sudo apt-get install startupmanager
```

---

### Post by Carthorse on 2010-09-03
Alternatively,
make a note of the position where the Windows listing appears on the grub boot screen, remembering the first entry will be '0', not '1'.
then in Ubuntu, 

sudo gedit /etc/default/grub

change the entry

GRUB_DEFAULT=0

to the number corresponding to the previously noted position of the Windows entry.
eg if your grub list on boot-up has Windows say, fourth down the list, change this entry to 
GRUB_DEFAULT=3

Don't forget to run update-grub when you've made the changes :-)

---

