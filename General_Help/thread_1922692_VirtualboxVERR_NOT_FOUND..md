---
title: "Virtualbox:VERR_NOT_FOUND."
date: 2012-02-09
forum: General Help
---

### Post by coreychbt8295 on 2012-02-09
p, li { white-space: pre-wrap; }  Could not load the Host USB Proxy service: VERR_NOT_FOUND.


any help would be appreciated, i was able to access my ipod on vb before i updated my kernel from 3 to 3.2  p, li { white-space: pre-wrap; }  
   Result Code: 
  NS_ERROR_FAILURE (0x00004005)
   Component: 
  Host
   Interface: 
  IHost {dab4a2b8-c735-4f08-94fc-9bec84182e2f}
   Callee: 
  IMachine {5eaa9319-62fc-4b0a-843c-0cb1940f8a91}

---

### Post by wbaccari on 2012-11-08
The vboxdrv kernel module is not loaded. Either there is no module available for the current kernel or it failed to load. Just recompile the kernel module and install it by:

          ```
 sudo /etc/init.d/vboxdrv setup
```

---

