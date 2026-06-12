---
title: "uhci-hcd module"
date: 2010-11-12
forum: General Help
---

### Post by Nipuna on 2010-11-12
I am Using Ubuntu since Ubuntu 8.04

I tried Ubuntu 10.10 on VirtualBox then It gave me another error message so I thought in Ubuntu 10.10 My Modem will work so I installed Ubuntu 10.10 as Dual Boot and tried installing Eciadsl but It gave me same error as on Ubuntu 10.04.


Here is the Error Message I get from Ubuntu 10.10 not from VB from real one

```
root@nipuna-OEM:~# eciadsl-start

[EciAdsl 1/5] Setting up USB support...

Preliminary USB device filesystem is missing... trying to mount
Preliminary USB device filesystem: failed to load
/usr/bin/eciadsl-start: line 263: fatal: command not found
cat: /proc/bus/usb/devices: No such file or directory
Loading UHCI support... Warning: uhci-hcd module doesn't exist
Warning: tun/tap module does not exist

[EciAdsl 2/5] Uploading firmware...

grep: /proc/bus/usb/devices: No such file or directory
grep: /proc/bus/usb/devices: No such file or directory
ERROR: modem not found
root@nipuna-OEM:~# 
```I think I have to install this    " uhci-hcd module  " 

i searched about this too but No Luck. :( 

I don't have internet on Ubuntu So Please tell me any other way to install this. I really need to install this to get internet to Ubuntu.  :(

Thanks

---

### Post by Nipuna on 2010-11-12
I really Need Help.

Please Help.

---

### Post by Nipuna on 2010-11-12
Bump

---

### Post by Nipuna on 2010-11-12
Please Help

I love Ubuntu but Because of this Problem i have to use Windows 

I really Need This.

---

### Post by frogotronic on 2012-05-17
> **Nipuna said:**
> Please Help

I love Ubuntu but Because of this Problem i have to use Windows 

I really Need This.

Try this: [https://help.ubuntu.com/community/Loadable_Modules](https://help.ubuntu.com/community/Loadable_Modules)

---

