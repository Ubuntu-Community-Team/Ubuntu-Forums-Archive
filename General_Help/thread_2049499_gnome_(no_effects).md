---
title: "gnome (no effects)"
date: 2012-08-28
forum: General Help
---

### Post by nagileon on 2012-08-28
Hi there,
Since some time ago I am not able to log on to my system with the usual gnome settings.
I need to choose gnome (no effects) otherwise the system kicks me out back to the log-on screen.

My system: 

cat /proc/version

Linux version 2.6.38-8-generic-pae (buildd@vernadsky) (gcc version 4.5.2 (Ubuntu/Linaro 4.5.2-8ubuntu3) ) #42-Ubuntu SMP Mon Apr 11 05:17:09 UTC 2011


cat /var/log/messages

Aug 28 23:28:17 pki kernel: [ 2710.711801] Xorg[17924]: segfault at 45 ip 080f3f74 sp bf951330 error 4 in Xorg[8048000+1ae000]Aug 28 23:28:17 pki kernel: [ 2710.711801] Xorg[17924]: segfault at 45 ip 080f3f74 sp bf951330 error 4 in Xorg[8048000+1ae000]


Please help.

---

### Post by wojox on 2012-08-28
Sounds like the video driver if no effects work okay. What do you have installed?

---

### Post by nagileon on 2012-08-28
*-display
                description: VGA compatible controller
                product: Madison [Mobility Radeon HD 5000 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:46 memory:b0000000-bfffffff memory:c4000000-c401ffff ioport:4000(size=256) memory:c4040000-c405ffff

 *-display
                description: VGA compatible controller
                product: Madison [Mobility Radeon HD 5000 Series]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
                configuration: driver=fglrx_pci latency=0
                resources: irq:46 memory:b0000000-bfffffff memory:c4000000-c401ffff ioport:4000(size=256) memory:c4040000-c405ffff

---

