---
title: "how to make one partition smaller, then add the rest to  main ( / )"
date: 2010-10-15
forum: General Help
---

### Post by AndreaZ on 2010-10-15
Hello everyone.
I have a dual-boot Vaio, with Windows Vista (for WOW only,I promise!) and Ubuntu 10.10.

I have a HDD with 250 GB, where 170GB is for Ubuntu and around 40 GB for Windows and a Swap that is 6 GB.

This Swap seems a little too big, so how o I edit it´s size (make it smaller like 3GB) and then add the "free space"-leftovers to the big Ubuntu partition ( / )?

It´s not the most important in the world, but I´d still like to know how to do it :)

Thanks :)

---

### Post by blueridgedog on 2010-10-15
Boot on the LiveCD then turn swap off from the terminal

```
sudo swapoff
```

Then use gparted to resize the swap partition, then the other partition in turn.  There are several tutorials for gparted online, here is one that covers resizing steps:

[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

---

### Post by AndreaZ on 2010-10-18
will try as soon as I get home.
Corerct me if I am wrong, but do I need 6 GB swap if I have 3GB RAM ?

---

### Post by Quackers on 2010-10-18
If you use hibernate you'll need a swap of about 3.1GB. If you don't use hibernate you probably won't even use swap - 1GB would almost certainly be enough.
When resizing swap be sure to leave the new unallocated space next to the partition you want to extend.

---

### Post by dcstar on 2010-10-18
> **AndreaZ said:**
> will try as soon as I get home.
Corerct me if I am wrong, but do I need 6 GB swap if I have 3GB RAM ?
**[SIZE="4"]NO![/SIZE]**

[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

