---
title: "Radeon hd3600 trouble"
date: 2011-01-30
forum: General Help
---

### Post by Paper183 on 2011-01-30
I know there are a lot of threads about those but i haven't seen one yet with the same problem as me I'm getting desperate. I have successfully installed ati's latest proprietary drivers (11.1) for the third time since i updated the kernel 2 times since first install, the restricted drivers utility tells me ati's drivers are in use but amdccce won't open and glxinfo in terminal never outputs anything else than:

> 
$ glxinfo
name of display: :0.0
^C


i have to press ctrl+c to make it stop... games wont work either most wont start at all... been searching uninstalling and reinstalling drivers for too much time now lol i need help :(

Edit: oops I'm on 10.10, forgot to mention, 32bit desktop

here's the output of another command maybe it helps...
> 
$ sudo lshw -C video
  *-display               
       description: VGA compatible controller
       product: Mobility Radeon HD 3600 Series
       vendor: ATI Technologies Inc
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:66 memory:c0000000-cfffffff memory:ff4f0000-ff4fffff ioport:c000(size=256) memory:ff4c0000-ff4dffff

the card is a desktop PCIE card i dont know why it says mobility... maybe just same chip ? that would suck

---

### Post by Paper183 on 2011-01-30
ive changed the title to be more relevant...

---

