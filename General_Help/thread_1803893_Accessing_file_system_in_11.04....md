---
title: "Accessing file system in 11.04..."
date: 2011-07-14
forum: General Help
---

### Post by Dunbahl on 2011-07-14
...when I load into Ubuntu 11.04 from my USB drive, why can't I access the files on my internal hard drive?

I mount the drive but I cannot see any of the music, videos or documents contained on that drive (which is also an Ubuntu 11.04 drive).

I was wondering so I could copy those files onto my external hard drive and reinstall since my Ubuntu crashed.

Thanks.

---

### Post by wildmanne39 on 2011-07-14
> **Dunbahl said:**
> ...when I load into Ubuntu 11.04 from my USB drive, why can't I access the files on my internal hard drive?

I mount the drive but I cannot see any of the music, videos or documents contained on that drive (which is also an Ubuntu 11.04 drive).

I was wondering so I could copy those files onto my external hard drive and reinstall since my Ubuntu crashed.

Thanks.Hi, check with disk utility and make sure it is mounted.

It maybe a permission problem so try this.

Livecd use a root

```
gksudo -i nautilus
```
opens the root file browser window in the live cd, no password required.
This should be the same with liveusb.
Thank you linuxman94 for catching that I knew that I just slipped a little there.

---

### Post by linuxman94 on 2011-07-14
You should be able to see the files even if there is a permission issue.  Furthermore you should use gksudo not sudo for graphical applications.  Are you going to the right path?  You should be in /home/(username)

---

### Post by Dunbahl on 2011-07-15
Thank you!!!  'gksudo -i nautilus' didn't work so I tried it with 'sudo -i nautilus'...worked like a charm!!!!!!!:KS

---

