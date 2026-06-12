---
title: "HELP!!  Unable to mount root filesystem?"
date: 2009-12-19
forum: General Help
---

### Post by vaiocomputer on 2009-12-19
Okay, well, I accidentally unplugged Ubuntu while it was running on my laptop (although the hard drive was not flashing at the moment), and now, it can't boot anymore: it goes to terminal and says something about not being able to load sbin/init.

So, I put a live CD in and sure enough, my root partition won't mount (Home partition fine, both ext3).
There's a popup that says: "mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sda7, missing codepage or helper program, or other error In some cases useful info is found in syslog - try dmesg | tail or so".

I entered that in Terminal and it says:

"$ dmesg | tail
sd 0:0:0:0: [sda] Sense Key  : Medium Error [current] [descriptor]
Descriptor sense data with sense descriptors (in hex):
        72 03 11 04 00 00 00 00 0c 00 0a 80 00 00 00 00 00 
        19 8f 3a 8e
sd 0:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
end_request: I/O error, dev sda, sector 428817038
atal: EH complete
JBD: Failed to read block at offset 24110
JBD: recovery failed
EXT3-fs: error loading journal."

I don't want to reinstall Ubuntu if possible.  There's alot of stuff in /... that I still want to keep.
Thanks.

---

### Post by wojox on 2009-12-19
[http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html](http://www.cyberciti.biz/tips/surviving-a-linux-filesystem-failures.html)

---

