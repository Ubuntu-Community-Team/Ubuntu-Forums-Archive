---
title: "problem in installing thc-hydra"
date: 2010-10-16
forum: General Help
---

### Post by ibtkm on 2010-10-16
hi all
i want to install hydra-5.4 from source . but at first in ./configure i have this problem : 
```
Checking for SAP/R3 (librfc/saprfc.h) ...
.. NOT found, module sapr3 disabled

```
 
i didn't want that in any place such as it's site.
how can i fix this problem?

---

### Post by david.maciejak on 2010-10-19
fyi Hydra is available at [http://freeworld.thc.org/thc-hydra/](http://freeworld.thc.org/thc-hydra/) latest version is 5.8 :)
This message means that the SAP module will be disabled as the Netweaver lib was not found, you can ignore this message if you don´t care about it or try to download an eval version at [http://www](http://www).*sap*.com/solutions/netweaver/linux/eval/index.asp ...

---

