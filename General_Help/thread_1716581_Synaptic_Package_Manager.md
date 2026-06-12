---
title: "Synaptic Package Manager"
date: 2011-03-28
forum: General Help
---

### Post by eipapp on 2011-03-28
When I try to run Synaptic Package Manager in Ubuntu 10.10 I get the following message:
 dpkg was interrupted, you must manually run sudo dpkg-configure-a to correct the problem. However when I do this nothing changes I still cannot access Synaptic Package Manager. What am I doing wrong ? How can I fix this ?

Regards,
Bruce

---

### Post by wojox on 2011-03-28
Try

```
sudo dpkg --configure -a
```

```
sudo apt-get install -f
```

---

### Post by eipapp on 2011-03-29
Worked like a charm ... Thank You, Thank You, Thank You !!!!!

---

