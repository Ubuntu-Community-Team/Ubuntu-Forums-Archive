---
title: "Can't install ubuntu on MSI A6000"
date: 2011-07-11
forum: General Help
---

### Post by Critical24 on 2011-07-11
I have a MSI A6000 and when I try to install Ubuntu it most of the time freezes on the installer. I cant even view it as a live CD. I get a error something long the lines of /DEV/SDA: ERROR or something a long those lines. I cant remember right off hand. I was wondering if anyone could help me with this.

Tech Specs:
[http://www.google.com/products/catalog?q=MSI+a6000&oe=UTF-8&hl=en&cid=7582142280861588779&os=tech-specs](http://www.google.com/products/catalog?q=MSI+a6000&oe=UTF-8&hl=en&cid=7582142280861588779&os=tech-specs)

I also burned the dvd using 2 different drives at the slowest speed.
I tried 1 blu-ray burner and 1 DVD-R

---

### Post by Mark Phelps on 2011-07-11
If you can't even boot from a LiveCD, there's not much we can do to get it installed that way.

Since your PC came with Win7 preinstalled, there's a possibility that it already has the maximum of four partitions configured -- in which case, the installer will be unable to create any more.

You could try downloading a GParted LiveCD from Distrowatch.com, burning it to CD, and booting from it.  Then, open the Partition Editor to see what partitions you have on your drive.

---

### Post by Critical24 on 2011-07-11
now i get a error that says  "/init: line 7: Cant open /dev/sdb/: No Medium Found"

---

