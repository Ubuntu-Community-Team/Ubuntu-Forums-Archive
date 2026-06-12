---
title: "Jaunty Kernal breaks USB HD and SD Reader on my comp"
date: 2009-06-26
forum: General Help
---

### Post by beattyml1 on 2009-06-26
Conditions:
[LIST]
[*]This problem happens with the Jaunty 2.6.28 kernal
[*]It does not happen in Juanty when running the Intrepid 2.6.27 kernal
[*]Does not work in either new install or jaunty upgraded from intrepid (when using kernal 2.6.28 )
[*]It does not happen with Mandriva spring 09 2.6.30 kernal
[/LIST]



Problem
[LIST]
[*]USB HD not detected
[*]Memory Card reader not detected
[/LIST]


Other info
[LIST]
[*]My 8 GB usb flash drive is detected
[*]When I insert my 8GB USB flash drive it causes the USB HD and the memory card reader to be detected
[*]USB HD and memory card reader are not even shown in /dev
[/LIST]


Any ideas/help?

---

### Post by beattyml1 on 2009-06-30
Anyone?

---

### Post by BambooClaw on 2009-07-04
I had trouble with USB flash drive not mounting.  The problem was that the module usb_storage was not being loaded by the OS.  So run
sudo modprobe -i usb_storage
before plugging in the drives and see if that works.  If so then a more permanent solution is to add usb_storage to the end of your /etc/modules file.

---

### Post by beattyml1 on 2009-07-04
That seems to have fixed it.  Thanks! :)

---

