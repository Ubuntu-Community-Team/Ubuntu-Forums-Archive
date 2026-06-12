---
title: "Ubuntu 10.04 in a VM on Win7 Ultimate - Not able to access shares..."
date: 2010-11-18
forum: General Help
---

### Post by bob4432 on 2010-11-18
new to ubuntu.  installed it as a vm in vmware workstation on win7ult 64bit (chose the 32bit version of ubuntu).  things are working very well w/ a few exceptions.  

i can not see the network shares from within the ubuntu vm and i also can not access the shares on the host machine even though they are setup in vmware to be shared w/ the ubuntu client.

in ubuntu, i can see the printer that is connected to the local host (which is a network shared printer), but i can not print to it.  i have run the samba install and configured the smb.conf file to reflect the correct workgroup, but no luck.  fwiw, the username/password i use to login to ubuntu is the same i use to login to the main machine.

any info on how i can access the local lan and also print from within the ubuntu vm would be greatly appreciated.

tia,
bob

---

### Post by krismatth3 on 2010-11-18
Have you installed the vm additions in ubuntu? Does the ubuntu machine otherwise have access to the internet?

How is your VMware network interface configured?

---

### Post by bob4432 on 2010-11-18
no, i was not aware that i needed to install anything related to vmware in ubuntu - i will look for that

the ubuntu machine has internet access, yes

in vmware, for network adapter it is listed as NAT.

---

### Post by bob4432 on 2010-11-20
not real sure what to install in ubuntu - any pointers?

---

### Post by bob4432 on 2010-11-23
anybody???

---

