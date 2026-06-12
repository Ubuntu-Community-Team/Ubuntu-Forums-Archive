---
title: "Boot file"
date: 2010-08-15
forum: General Help
---

### Post by d_darlac on 2010-08-15
Hi all, 

in Ubuntu 10.04 I installed VMware workstation 7.1 to run a VM - everytime I need to run it though, Workstation doesn't find a file (VMmon) and  I need to run in terminal this command:
sudo /etc/init.d/vmware start

how can I add this in the boot file so it starts automatically and I do not have to run it manually -

---

### Post by d_darlac on 2010-08-20
For anyone with the same problem - 

the solution was to uninstall VMware
then, after un-installing you have to manually remove 
- /usr/tmp (anything regarding VMware)
- /var/log/vmware-installer

that worked for me

---

