---
title: "NBD drive hangs"
date: 2009-11-25
forum: General Help
---

### Post by yeeeev on 2009-11-25
I'm not sure this is the right place to post this, but still...
I'm using an nbd drive as my backup device. ([http://code.google.com/p/sc101-nbd/](http://code.google.com/p/sc101-nbd/))
Everything works well when I connect it. After a while (a few hours, usually during large transfers) the /dev/nbd0 device hangs.
I cannot unmount it, cannot remount it as another device, and eventually every process that tries to read the device simply hangs...
What is the best way to start debugging this issue? Is there some way I can look at the loaded devices status, related system calls and try to realize what is going on?

Thanks!

---

