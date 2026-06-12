---
title: "partition help"
date: 2009-11-06
forum: General Help
---

### Post by mikeonthebeach on 2009-11-06
okay i just installed ubuntu 8.04 on my computer, i installed it side by side with windows. when i try to download stuff i get an error message saying there is no space left on my drive. how do i set aside more hard drive space?

---

### Post by dcstar on 2009-11-06
> **mikeonthebeach said:**
> okay i just installed ubuntu 8.04 on my computer, i installed it side by side with windows. when i try to download stuff i get an error message saying there is no space left on my drive. how do i set aside more hard drive space?

You do a forum search for extending partitions and follow the various instructions in the solutions.

---

### Post by pastalavista on 2009-11-06
> **dcstar said:**
> You do a forum search for extending partitions and follow the various instructions in the solutions.

That was about the snarkiest response I've ever heard on here.. smart-***

Boot the live CD (try without changes) and open System-> Administration-> Partition Editor (Gparted). Right-click on the Windows partition and unmount and resize/shrink and then Right-click
the Ubuntu partition and unmount and resize/expand.

---

### Post by mikeonthebeach on 2009-11-06
> **pastalavista said:**
> That was about the snarkiest response I've ever heard on here.. smart-***

Boot the live CD (try without changes) and open System-> Administration-> Partition Editor (Gparted). Right-click on the Windows partition and unmount and resize/shrink and then Right-click
the Ubuntu partition and unmount and resize/expand.



thank you, i just installed gparted but when i try to open it, i get an error message saying " Failed to run/usr/sbin/gparted as user root, Unable to copy the user's Xauthorization file"

---

### Post by pastalavista on 2009-11-07
> **mikeonthebeach said:**
> thank you, i just installed gparted but when i try to open it, i get an error message saying " Failed to run/usr/sbin/gparted as user root, Unable to copy the user's Xauthorization file"
Are you using the live CD? You won't be able to use gparted on a mounted drive. Gparted is included on the live CD. And to run commands with root permissions you need to prefix the command with 'sudo' or in the case of graphical apps use 'gksu'.

```
gksu gparted
```

---

