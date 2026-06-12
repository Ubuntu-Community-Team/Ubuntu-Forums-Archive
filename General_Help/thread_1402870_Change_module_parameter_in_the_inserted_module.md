---
title: "Change module parameter in the inserted module"
date: 2010-02-09
forum: General Help
---

### Post by alecm3 on 2010-02-09
I need do change a module parameter on the module that is already inserted in the kernel. What is the least invasive way to do this, since it's on a production machine that I cannot reboot?
I was going to do
```
modprobe -r ipt_recent
modprobe ipt_recent ip_list_tot=500
```
(I need to change ip_list_tot parameter)
but I get 
```
# modprobe -r ipt_recent
FATAL: Module ipt_recent is in use.
```

---

