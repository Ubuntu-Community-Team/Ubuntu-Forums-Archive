---
title: "problem in installing java-sdk!!"
date: 2009-08-14
forum: General Help
---

### Post by harivittal.hk on 2009-08-14
hi!! 
i am trying to install java in terminal,i ran the cmd:sudo apt-get install openjdk-6-jre
then thr was an error:"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem."
dpkg: requested operation requires superuser privilege

when i gave "su" ,it showed: 
"su: Authentication failure"
how can i correct this .
any help is appreciated!!:)

---

### Post by credobyte on 2009-08-14
```
sudo dpkg --configure -a
```

Regarding su authentication failure - by default, root account is disabled. 
Use ( relies on sudoers file ):
```
sudo -i
```

---

