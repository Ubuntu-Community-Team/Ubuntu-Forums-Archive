---
title: "automatically mount ntfs partitions at boot time"
date: 2009-09-06
forum: General Help
---

### Post by prakreet on 2009-09-06
I want to configure my ubuntu 9.04 to automatically mount my 4 ntfs drives at boot time to /windows/(c,d,e,f). Please help me....

---

### Post by Elfy on 2009-09-06
Install ntfs-config - search in add/remove for it or eaasily install from the terminal

```
sudo apt-get install ntfs-config
```

It will have a menu entry under System Tools - run that and it will allow you to get your ntfs drives mounting on boot.

[https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G](https://help.ubuntu.com/community/MountingWindowsPartitions/ThirdPartyNTFS3G)

---

