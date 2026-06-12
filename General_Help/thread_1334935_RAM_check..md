---
title: "RAM check."
date: 2009-11-22
forum: General Help
---

### Post by Ubu4moi on 2009-11-22
The system info says I got only 3.7gb of RAM but I have 4 installed. How can I know where the rest of it is? I'm running Ultimate Edition 2.0 64bit on an HP Pavilion AMD Athlon 2X.

---

### Post by Scott753 on 2009-11-23
That looks about right. You have a 64-bit system so the total amount of memory that can be addressed is more than 4GB (depends on the OS). Within that address range, there are also the system I/O devices and other hardware. These in effect take up some of the available memory space, so the amount of physical memory available to your system actually reduces by that amount. Depending on your system's hardware and configuration, this can be anything ranging from 256MB to 1GB (typically 768MB). However, that can vary. In addition, the GPU is allocated a portion of your RAM for its own use.

---

