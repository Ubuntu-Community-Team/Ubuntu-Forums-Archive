---
title: "Ubuntu 9.10 doesn't detect USB drives"
date: 2009-11-22
forum: General Help
---

### Post by uv2008 on 2009-11-22
Hello,

After upgrading to Ubuntu 9.10 64 bit the USB drives are not being detected - this is a problem that didn't exist at Ubuntu 9.04, and the drives work fine on Windows and Mac.

I'd be grateful for any suggestion.

---

### Post by SPr on 2009-11-22
what do 
```
dmesg|tail
```
and
```
lsusb
```
report after plugging in the drives.

---

### Post by uv2008 on 2009-11-25
Thanks for your attempt to help. After having several after severe problems after upgrading (mostly about system freezing and graphics problems) I decided to reinstall Ubuntu 9.10 and everything works perfect now, so something must have gone wrong in the process of upgrading from 9.04 to 9.10...

---

### Post by victor.zamanian on 2009-11-25
I think it might just have been an update that arrived between the last failure to detect the drive and you reinstalling. I had the same problem, but it's not happening anymore, it seems, and I haven't reinstalled the OS.

Something that's worth mentioning is that whenever it would happen (the non-detection), logging out and then back in would make it detect the drives again. So if it ever happens again, try that in the meantime and pray for a software update soon. :-)

---

