---
title: "virtualbox help"
date: 2011-08-27
forum: General Help
---

### Post by kc_mint88 on 2011-08-27
i have been using both Ubuntu and mint for the past 2 years i often try new stuff i am interested in using virtulization software in mint to eliminate the "dual Boot" that i have been dealing with for 2 years i have virtualbox on my mint computer and i am ready to get started i just didn't know if anyone had any helpful tips or tricks that may avoid any problems for me

---

### Post by YesWeCan on 2011-08-28
I use VB all the time, it's generally excellent.
Download it from [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)
Don't forget the extensions pack
Allocate at least 1GB for the Ubuntu guest
Unity won't run at all without guest additions and allocate max video memory
I always choose dynamically expanding disk drives (the default)
You cannot make a disk bigger so choose a big size to start with.
Read the manual, it is very good: [http://www.virtualbox.org/manual/UserManual.html](http://www.virtualbox.org/manual/UserManual.html)

---

### Post by kc_mint88 on 2011-08-29
K did all of that and still no VM i am getting this error from my install  

Please Help i have made it too far to quit now
 p, li { white-space: pre-wrap; }  00:00:00.284 VirtualBox 4.0.6 r71344 linux.amd64 (Apr 21 2011 11:22:00) release log
 00:00:00.284 Log opened 2011-08-29T06:36:08.657456000Z
 00:00:00.284 OS Product: Linux
 00:00:00.284 OS Release: 2.6.38-8-generic
 00:00:00.284 OS Version: #42-Ubuntu SMP Mon Apr 11 03:31:24 UTC 2011
 00:00:00.285 DMI Product Name: System Product Name
 00:00:00.285 DMI Product Version: System Version
 00:00:00.285 Host RAM: 7749MB RAM, available: 6576MB
 00:00:00.285 Executable: /usr/lib/virtualbox/VirtualBox
 00:00:00.285 Process ID: 30058
 00:00:00.285 Package type: LINUX_64BITS_UBUNTU_11_04
 00:00:00.344 pdmR3LoadR0U: pszName="VMMR0.r0" rc=VERR_SUPLIB_WORLD_WRITABLE szErr="World writable: '/usr'"
 00:00:00.344 VMSetError: /home/vbox/vbox-4.0.6/src/VBox/VMM/VMMR3/VM.cpp(583) int vmR3CreateU(UVM*, uint32_t, int (*)(VM*, void*), void*); rc=VERR_SUPLIB_WORLD_WRITABLE
 00:00:00.344 VMSetError: Failed to load VMMR0.r0
 00:00:00.344 VMSetError: /home/vbox/vbox-4.0.6/src/VBox/VMM/VMMR3/VM.cpp(354) int VMR3Create(uint32_t, const VMM2USERMETHODS*, void (*)(VM*, void*, int, const char*, unsigned int, const char*, const char*, __va_list_tag*), void*, int (*)(VM*, void*), void*, VM**); rc=VERR_SUPLIB_WORLD_WRITABLE
 00:00:00.344 VMSetError: Unknown error creating VM
 00:00:00.344 ERROR [COM]: aRC=NS_ERROR_FAILURE (0x80004005) aIID={515e8e8d-f932-4d8e-9f32-79a52aead882} aComponent={Console} aText={Failed to load VMMR0.r0 (VERR_SUPLIB_WORLD_WRITABLE).
 00:00:00.344 Unknown error creating VM (VERR_SUPLIB_WORLD_WRITABLE)}, preserve=false
 00:00:00.358 Using XKB for keycode to scan code conversion
 00:00:00.410 Power up failed (vrc=VERR_SUPLIB_WORLD_WRITABLE, rc=NS_ERROR_FAILURE (0X80004005))

---

