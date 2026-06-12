---
title: "/media missing, can't mount ANYTHING! Please Help!!"
date: 2010-06-18
forum: General Help
---

### Post by Cfhs_1 on 2010-06-18
Hello everyone,

I seem to have messed things up pretty bad this time, I was following this guide:

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)

Well I was following the first solution that used the scripts.

It worked fine at first, I could mount and unmount ISO's like any CD.
Then I guess I forgot to unmount one that was in my windows partition and rebooted. Now my whole /media folder doesn't exist, and I can't mount ANYTHING! CDs, Flash drives, Memory Cards, ISOs, nothing! Can someone PLEASE PLEASE help me!!

---

### Post by WorMzy on 2010-06-18
If /media doesn't exist, you can remake it by running ```
sudo mkdir /media
```

---

### Post by 98cwitr on 2010-06-18
yeah, just recreate /media

---

### Post by dcstar on 2010-06-18
> **Cfhs_1 said:**
> Hello everyone,

I seem to have messed things up pretty bad this time, I was following this guide:

[http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html](http://www.ubuntugeek.com/mount-and-unmout-iso-images-without-burning-them.html)
........

WHY??? all you have to do is right-click the ISO and "Open with" the Archive Mounter.

It is all built into 10.04, there is no need whatsoever to follow ancient HOWTOs from 2006.

---

### Post by Cfhs_1 on 2010-06-18
> **WorMzy said:**
> If /media doesn't exist, you can remake it by running ```
sudo mkdir /media
```

Thanks! Now I can finally play Halo: CE

---

### Post by Cfhs_1 on 2010-06-18
> **dcstar said:**
> WHY??? all you have to do is right-click the ISO and "Open with" the Archive Mounter.

It is all built into 10.04, there is no need whatsoever to follow ancient HOWTOs from 2006.


yea, I realized that after I had Mucked things up. lol.

---

### Post by Cfhs_1 on 2010-06-18
Thanks for all your help guys! This is exactly why I love the ubuntu community!! Problem solved.

---

### Post by TristanCharles on 2011-01-24
I also had this problem. But solved by this thread. Thanks!

---

