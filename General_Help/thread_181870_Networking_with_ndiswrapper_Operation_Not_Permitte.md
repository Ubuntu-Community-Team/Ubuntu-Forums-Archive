---
title: "Networking with ndiswrapper: Operation Not Permitted"
date: 2006-05-24
forum: General Help
---

### Post by DJ Scribblinni on 2006-05-24
Hows it going everybody.  After a reinstall of Breezy, I'm struggling to get my wireless card to work on my PC.  It is the wonderful Linksys WMP11 v2.7 with the infamous broadcom chipset.  I've used ndiswrapper last time, and it worked beautifully, I amazed myself.  Now after the reinstall, I'm doing a 'sudo modprobe ndiswrapper' with this output: 
'FATAL: Error inserting ndiswrapper (/lib/modules/2.6.12-9_386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko); Operation not permitted'

I've done everything the exact same way I did months ago.  If there are some log files, or commands that can be looked at please let me know.  This oldie computer has no ethernet, nor is it possible to run a wire around this house, which equals me being desperate at this point in time.  Frustrating, it used to work.  Grrr.

For the curious, I've used the drivers that came with the cd, I found another website that provided drivers, and tried some other drivers I found on another Thread (can't find that tread anymore...),,,nothing has worked, same error;  But as always the driver is present, hardware is present....

I even tried upgrading to Dapper, no luck.  Computers are fun, computers are fun computers are fun...

Have a great day! :)

---

### Post by az on 2006-05-25
You can get that error if the .inf file is not the appropriate one for your device.

---

