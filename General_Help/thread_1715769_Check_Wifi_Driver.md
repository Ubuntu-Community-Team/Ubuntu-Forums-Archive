---
title: "Check Wifi Driver"
date: 2011-03-27
forum: General Help
---

### Post by cap10Ibraim on 2011-03-27
How can I know what  driver is installed for my intel wireless card ?

---

### Post by Enigmapond on 2011-03-27
I think the terminal command is:

```
lspci
```

---

### Post by mikewhatever on 2011-03-27
You can check with the following command:
```
sudo lshw -C network | grep driver
```

---

### Post by cap10Ibraim on 2011-03-27
I want to know if it is one of those grep can't find it with lspci 
```

ipw2100           Kernel Intel 2100 driver
ipw2200           Kernel Intel 2200 driver
ipw2915           Kernel Intel 2915 driver
ipw3945           Kernel intel 3945 driver

```

---

### Post by cap10Ibraim on 2011-03-27
> **mikewhatever said:**
> You can check with the following command:
```
sudo lshw -C network | grep driver
```

thanks this worked

---

### Post by mikewhatever on 2011-03-27
Yea, lspci only shows the card model, but not the driver.
;)

---

