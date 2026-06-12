---
title: "dosemu parallel port bit twiddling?"
date: 2010-06-01
forum: General Help
---

### Post by wkulecz on 2010-06-01
I've been running an old DOS app that reads and writes the parallel port bits to do a control task.  Its worked great running on Ubuntu 6.06 but I can't get the version on 10.04 to read and write the actual hardware.

I can't find what is missing from the configuration, as I recall all I did on 6.06 was edit /etc/dosemu/dosemu.conf to uncomment the line:

$_ports = $_ports, " device /dev/lp0 range 0x378 0x37a"

in the "Direct Hardware access" section and start the xdosemu session as root.  The process runs in the background and has "just worked" for years.  

This has got me stuck as the last step of migrating from 6.06 to 10.04 -- everything except this, postfix, samba, etc. couldn't have been easier, but I'm stuck now :(

Yes the new motherboard parallel port is set for 0x378 and it shows in /proc/ioports.  I guess it could be defective, but the software reads back the values it writes and thinks its working, its just none of the outputs change and changes on the inputs are not read so the code is stuck waiting for the initial response to its first output.

Anyone know what has changed in 10.04 that is preventing dosemu from twiddling actual bits?

--wally.

---

### Post by wkulecz on 2010-06-04
Figured it out, starting dosemu as root is not enough to enable raw port access after enabling it in dosemu.conf, you have to start as dosemu -s

Not sure, and don't really care, where this change was introduced, but its another one of those changes that offer only pain with zero gain.

--wally.

---

