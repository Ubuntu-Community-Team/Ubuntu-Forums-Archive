---
title: "problem with remastersys"
date: 2010-02-04
forum: General Help
---

### Post by switch10 on 2010-02-04
I have tried both of these:

```
sudo remastersys dist
```
```
sudo remastersys backup
```

I've tried on both my 64 bit and 32 bit systems.  The .ISO comes out fine without any errors.  When I try to boot the DVD, I get:

```
could not find ramdiskimage: /casper/initrd.gz
```

I have tried this several times on both systems and I get the same error.  I've also tried to boot the ISO images with Virtual box. 
Anyone know what is going on here?   

Thanks

Dave

---

### Post by switch10 on 2010-02-04
any ideas??

---

### Post by switch10 on 2010-02-04
I fixed it.  There was an updated repository for Karmic.  I was using an older one.  I found this on the remastersys forums.

Here is the repository you should use for Karmic/Grub2:

```
deb http://www.geekconnection.org/remastersys/repository karmic/
```

---

