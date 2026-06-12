---
title: "portmap not running after boot"
date: 2010-06-11
forum: General Help
---

### Post by OkoSanto on 2010-06-11
Hi,

Using Lucid/10.04, I want the portmap service to start automatically at boot time, but can not get this to work.  Presumably it has to do with upstart?

Currently, my /etc/init/portmap.conf file contains

```
start on (virtual-filesystems
          and net-device-up IFACE=lo)

```

But that doesn't seem to work.  Don't understand what is wrong here, where should I look for a solution?

---

