---
title: "In Lucid again: VMWare Server - Remote USB device error"
date: 2010-05-13
forum: General Help
---

### Post by jstammi on 2010-05-13
Hi,

same again as in [http://ubuntuforums.org/showthread.php?t=1210625:](http://ubuntuforums.org/showthread.php?t=1210625:)
 - ubuntu lucid host (vmware server 2.0.2 x86_64)
 - windows xp vm
 - plug in usb stick to host
 - try to enable usb stick in vm console menu
=> "Remote USB device error: Remote device disconnected: an error occured while sending data."


In karmic the above ref'ed solution worked for me. But with 10.04 this is no longer possible as /proc/bu/usb no longer exists ...

Any ideas on this? Or does somewhere it is possible to attach an usb stick to a windows vm? If so: by what way exactly?

jstammi

---

### Post by elspringer on 2010-05-27
I have the exact same issue... With the USB directory gone that fix no longer works and I couldn't find another directory specific to USB to whare Icould just change path statements. If anyone has ideas or suggestions I am open... Thank you.
 
Okay I've done more research... What I have found so far:

VMware Server User's Guide says If your host operating system uses a different path to the USB device to mount it to /proc/bus/usb. 

Two problems there: 
1) /proc isn't a real directory so you can create the usb directory to mount to 
2) Ubuntu 10.04 has done away with usbfs and now uses ext4 which I believe can be found in /proc/fs/ext4... but if i'm correct this includes more than just the USB devices. 

Any suggestions on how to proceed or things I could try? 

I also have a simular post at:[http://communities.vmware.com/message/1542086](http://communities.vmware.com/message/1542086)
 
 Thanks for any help ahead of time...

---

### Post by dcstar on 2010-05-27
Please post **all** VM questions in the Virtualization forum.

---

