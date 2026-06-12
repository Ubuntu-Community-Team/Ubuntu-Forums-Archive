---
title: "Monitor resolution not supporting."
date: 2011-02-11
forum: General Help
---

### Post by samresh on 2011-02-11
Hi all,
        I installed ubuntu 10.10 but the resolution of my monitor not supported by ubuntu. initially I got message while installing "resolution out of range" then after installation resolution stuck-ed at 1024*768 and unable to increase it below are the details of configuration.

administrator@ubuntu:~$ sudo lshw -C video 
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: K8M800/K8N800/K8N800A [S3 UniChrome Pro]
       vendor: VIA Technologies, Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 01
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller bus_master cap_list
       configuration: latency=32 mingnt=2
       resources: memory:f0000000-f3ffffff memory:f4000000-f4ffffff memory:f5000000-f500ffff
administrator@ubuntu:~$

---

