---
title: "Virtual Box, grayed USB"
date: 2009-11-15
forum: General Help
---

### Post by 3Miro on 2009-11-15
I am using VB 3.0 from sun's repository. I have added myself to the virtual box usergroup.

I want to run my printer under VirtualBox kubuntu 9.10 amd64 host + windowsXP 32-bit client. When I try to connect to the printer I see 4 devices, 3 are camera, fingerprint reader and unknown and can be selected, the forth is the printer and is grayed out. Selecting and deselecting the filter, rebooting the host, the client and the printer have no effect.

When I run VirtualBox as root (kdesudo), I can select all 4 devices and run with either one. Printer works fine.

Does anyone know what is happening?

Appreciate the help.

```
VBoxManage list usbhost 
```

returns only the printer as unavailable.

---

### Post by 3Miro on 2009-11-15
Talking to myself here, but I hoe this helps someone who finds this page:

Add yourself to the ld group, then reboot the host. This fixes the Printer + Virtual box issue.

---

