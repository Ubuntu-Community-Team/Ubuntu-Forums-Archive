---
title: "pulling hair out over graphics not working"
date: 2011-10-20
forum: General Help
---

### Post by Helen84 on 2011-10-20
I cannot for the life of me get enable "extra" visual effects on my ubuntu 10.10. My hardware is not that great  VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)  but it should be good enough to handle desktop effects. I have done countless google searces and every result I find are bugs on launchpad and or questions about laptops. I trued installing the latest kernel (well, 3.0) and that made no difference either. i also applied all updates and upgrades. the error message i get "Desktop effects could not be enabled" is not very helpful either. 

root@hellen-ubuntu:~$ lspci -v -s 00:02.0; lspci -v -s 01:00.0
00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Micro-Star International Co., Ltd. Device 7680
    Flags: bus master, fast devsel, latency 0, IRQ 40
    Memory at fe000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at f000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

root@helen-ubuntu:~$

---

### Post by bibble235 on 2011-10-20
[http://ubuntuforums.org/showthread.php?t=1707760](http://ubuntuforums.org/showthread.php?t=1707760)

---

### Post by Helen84 on 2011-10-21
> **bibble235 said:**
> [http://ubuntuforums.org/showthread.php?t=1707760](http://ubuntuforums.org/showthread.php?t=1707760)

thanks ... interesting. but it didnt work. im not quite 100 % sure on the problem. so i have to change one of the numbers in each 8086:**** set something else? anyway i changed all 8 characters in each set of 8086:**** to 0 and saved it. it hasnt solved the problem. but it seems maybe you are on the right track ... i dont understand this at all is there an easier way that does not involve editing a binary file? this is a total hack ..

---

### Post by Helen84 on 2011-10-21
Never mind .. I switched to Mint and everything works great! So long Ubuntu! ):P

---

### Post by kaldor on 2011-10-21
Just a thought, but Sandybridge was dodgy back on Ubuntu 10.10.

I'd assume that 11.10 will work just fine right now. Mint is based on Ubuntu 11.04, so that explains the improvements.

---

