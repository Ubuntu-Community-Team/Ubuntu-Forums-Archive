---
title: "Disabling Zen Server at boot"
date: 2011-06-06
forum: General Help
---

### Post by nexul on 2011-06-06
Hi,

I can't figure out how to prevent Zend Server starting at boot up. 

My temporary solution is to issue the following after boot-up:

   ```
 sudo /usr/local/zend/bin/zendctl.sh stop 
```Ideally, I'd like to:

1. Prevent it from starting during boot
2. Create two launcher icons to Start and Stop Zend Server 

Does anyone know how to do this?

Thank's.
N.

---

### Post by sisco311 on 2011-06-07
Hi,

I don't use it, but it looks like zend server is started by a System-V stile init script, so you should be able to disable it with:
```
sudo update-rc.d zend-server remove
```
and (re-)enable it with:
```
sudo update-rc.d zend-server defaults
```

HTH

---

