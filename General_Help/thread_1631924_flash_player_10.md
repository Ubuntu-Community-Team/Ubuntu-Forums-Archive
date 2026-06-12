---
title: "flash player 10"
date: 2010-11-27
forum: General Help
---

### Post by gufide on 2010-11-27
Hi, I have flash player 10 but some application flickering and don't get draw correctly. No one solved this?

---

### Post by gordintoronto on 2010-11-27
I've never had those problems. Perhaps you could describe what version of Ubuntu you are using, how you installed Flash and what CPU and video card you have?

---

### Post by karthick87 on 2010-11-27
Post your outputs of these commands,

```
sudo lshw -C display
```

```
lsb_release -a
```

---

### Post by gufide on 2010-11-27
```
master@comput1:~$ sudo lshw -C display
  *-display               
       description: VGA compatible controller
       product: GT215 [GeForce GTS 360M]
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a2
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:f2000000-f2ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:d000(size=128) memory:f3000000-f307ffff

```

```
master@comput1:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 10.10
Release:    10.10
Codename:    maverick

```

it's ok?

---

