---
title: "Need the defaults for ..."
date: 2006-03-11
forum: General Help
---

### Post by brooklynlou on 2006-03-11
Crewed up the following files:

/etc/esound/esd.conf 
/etc/libao.conf 

Can someone post the defaults?

Thanks

---

### Post by dcstar on 2006-03-11
[QUOTE=brooklynlou]Crewed up the following files:

/etc/esound/esd.conf 
/etc/libao.conf 

Can someone post the defaults?

Thanks[/QUOTE]
Don't know about defaults, but this is what my system has:

```
[esd]
auto_spawn=0
spawn_options=-terminate -nobeeps -as 5
spawn_wait_ms=100
# default options are used in spawned and non-spawned mode
default_options=-as 5
```

```
default_driver=esd
```

---

