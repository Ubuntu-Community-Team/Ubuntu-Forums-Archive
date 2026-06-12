---
title: "Wavy screen on 8.04"
date: 2009-08-05
forum: General Help
---

### Post by TunaMloohnah on 2009-08-05
I just installed Ubuntu 8.04 on my laptop, and the screen is wavy and hard to read.  The resolution is also wrong.  Can anybody help?

It's an ati radeon xpress 1155, By the way

---

### Post by lildigiman on 2009-08-06
If you can read the screen well enough (and are familiar with ubuntu) try installing ATI's proprietary driver through System -> Admin -> Hardware drivers.

You can also try booting in safe mode (recovery mode), start the command line, typing: ```
sudo apt-get install xorg-driver-fglrx
```

Hope this helps. It should...

---

