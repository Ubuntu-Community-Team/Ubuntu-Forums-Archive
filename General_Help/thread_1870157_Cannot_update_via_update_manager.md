---
title: "Cannot update via update manager"
date: 2011-10-26
forum: General Help
---

### Post by elrod on 2011-10-26
Maverick. Following occurs after download and hitting install updates. Has worked for over a year. not sure what changed!

installArchives() failed: /var/cache/apt/archives /
/
xhost

---

### Post by wolfen69 on 2011-10-26
Try 
```
sudo apt-get clean
```

---

### Post by elrod on 2011-10-27
That did it. Thanks.

---

### Post by raja.genupula on 2011-10-27
whats the cause for this ?

---

### Post by zane131 on 2011-10-27
I am not sure if this is anything of value, but I had the same problem on Natty logged in under "Ubuntu Classic (no effects)". When I logged in under "Ubuntu" (Unity desktop), I did not have the problem. 

With that said the problem completely went away when I ran 'sudo apt-get clean' as stated above.

---

