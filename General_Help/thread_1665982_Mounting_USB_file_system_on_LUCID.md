---
title: "Mounting USB file system on LUCID"
date: 2011-01-13
forum: General Help
---

### Post by srinidhi.kv on 2011-01-13
Hi ,
This is Srinidhi, I wan to mount a custom hardware's USB file system. I am using Lucid Lynx.
When I used the command
$ sudo mount -t usbfs none /proc/bus/usb
There was an error as there was no
/proc/bus/usb

I tried to put it in fstab entry so that /proc/bus/usb will be mounted at boot 
but no luck.

How do I fix this? Any pointers on how to mount usb fs will be of gr8 help

Thanks in Advance
Srinidhi KV

---

### Post by Mark Phelps on 2011-01-13
I don't think you can mount to /proc.  Try mounting to /media instead.

---

### Post by srinidhi.kv on 2011-01-17
Hi Mark,
Thanks for the reply

When I try to mount USBFS to /media I get the below error

root@srinidhi-desktop:/home/srinidhi# mount -t usbfs none /media/
mount: unknown filesystem type 'usbfs'

Does kernel does not support USB file system?

Thanks
Srinidhi

---

