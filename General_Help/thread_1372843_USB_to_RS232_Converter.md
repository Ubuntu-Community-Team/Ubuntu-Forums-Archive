---
title: "USB to RS232 Converter"
date: 2010-01-05
forum: General Help
---

### Post by chathar on 2010-01-05
on ubuntu, when i plug in my USB to RS232 Converter, i receive following lines and unable to access it:
 
[ 67.391263] usb 2-1: device descriptor read/64, error -71
[ 67.630018] usb 2-1: device descriptor read/64, error -71
[ 67.990018] usb 2-1: device descriptor read/64, error -71
[ 68.230014] usb 2-1: device descriptor read/64, error -71
[ 68.880015] usb 2-1: device not accepting address 4, error -71
[ 69.420011] usb 2-1: device not accepting address 5, error -71
[ 69.420071] usb 2-0:1.0 unable to enumerate USB device on port 1
 
kindly advise, how to make it accessible on my ubuntu box.
 
also, i am running vmware server on this ubuntu box, will i be able to access this harware on my vmware guest?

---

### Post by dcstar on 2010-01-05
> **chathar said:**
> on ubuntu, when i plug in my USB to RS232 Converter, i receive following lines and unable to access it:
 
[ 67.391263] usb 2-1: device descriptor read/64, error -71
[ 67.630018] usb 2-1: device descriptor read/64, error -71
[ 67.990018] usb 2-1: device descriptor read/64, error -71
[ 68.230014] usb 2-1: device descriptor read/64, error -71
[ 68.880015] usb 2-1: device not accepting address 4, error -71
[ 69.420011] usb 2-1: device not accepting address 5, error -71
[ 69.420071] usb 2-0:1.0 unable to enumerate USB device on port 1
 
kindly advise, how to make it accessible on my ubuntu box.
 
also, i am running vmware server on this ubuntu box, will i be able to access this harware on my vmware guest?

You can try it the same way as any other USB device in VMware.

---

### Post by chathar on 2010-01-05
That's true, but as per error, when ubuntu is not detecting it, how can i use it in VM Guest Machine?

---

