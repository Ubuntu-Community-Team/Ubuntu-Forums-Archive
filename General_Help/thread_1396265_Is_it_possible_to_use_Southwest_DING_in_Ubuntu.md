---
title: "Is it possible to use Southwest DING in Ubuntu?"
date: 2010-02-01
forum: General Help
---

### Post by TracyO on 2010-02-01
Has anyone successfully gotten Southwest DING (an application from Southwest airlines) to work in Ubuntu?  I attempted via Wine, but it didn't work.

I use Hardy.

Thanks!

---

### Post by euphline on 2010-09-20
> **TracyO said:**
> Has anyone successfully gotten Southwest DING (an application from Southwest airlines) to work in Ubuntu?  I attempted via Wine, but it didn't work.

I use Hardy.

Thanks!

Running lucid, I followed the instructions here:
[http://ubuntuforums.org/showthread.php?t=477548](http://ubuntuforums.org/showthread.php?t=477548)

And I had success.  Here's what I learned:

ies4linux requires its own wine "program tree", generally ~/.ies4linux/ie6/drive_c/...  This threw me initially, as I'd already installed Ding unsuccessfully in the "main" tree.  Once I installed ies4linux, ran ie6 (~/bin/ie6), ran the Ding Installer, all was good.  I built the little script mentioned in the above forum post and whammy, it worked!

-jbn

---

