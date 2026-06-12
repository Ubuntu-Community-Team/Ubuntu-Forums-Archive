---
title: "USB HID(Controller) Not Reconized When Plugged In"
date: 2012-09-05
forum: General Help
---

### Post by T31337 on 2012-09-05
I am running Ubuntu 10.04, I Have USB SNES Controller That works percectly under windows but when I plug it into ubuntu I am unable to use it, But My XBOX Controller works under ubuntu just fine so there is nothing wrong with my usb ports. When I Try To Use my usb snes controller ubuntu ignores it. any help would be greatly appreciated
----------------------------------------------------------------------------------------------------------
lsusb outputs the following when i plug in my snes conroller:

Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 8086:0186 Intel Corp. 
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
------------------------------------------------------------------------------------------------------
 and without my snes controller the output looks like this:
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 8086:0186 Intel Corp. 
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
-------------------------------------------------------------------------------------------------------
 but with my xbox controller the output looks like this:

Bus 002 Device 008: ID 1bad:f016 Harmonix Music 
Bus 002 Device 002: ID 8087:0020  
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 8086:0186 Intel Corp. 
Bus 001 Device 003: ID 04f2:b1d6 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020  
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

:confused::confused::confused:

(I use the zsnes emulator)

---

### Post by T31337 on 2012-10-10
My Controller stopped working in windows too If I Plug it in to any os it does nothing so I believe it to be broken this thread can be deleted please. ):P

---

