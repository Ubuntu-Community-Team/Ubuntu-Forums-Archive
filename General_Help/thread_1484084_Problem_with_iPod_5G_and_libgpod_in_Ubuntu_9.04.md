---
title: "Problem with iPod 5G and libgpod in Ubuntu 9.04"
date: 2010-05-15
forum: General Help
---

### Post by lgsilveira on 2010-05-15
Hello

This week I've got a 16GB iPod nano.  I connected it to my PC and rhythmbox offered to initialize it, I said OK, and shortly after I was loading songs into it. But my iPod couldn't find any song. A tried with gtkpod and the same happened. Then, I found out that the libgpod version I was using (0.7.0) didn't support 5G nanos. So I dowloaded libgpod 0.7.93 and gtkpod 0.99.16 sources and compiled them. Now, when I try to sync it in gtkpod I got this:

Extended Info will not be used
iPod database import failed
Newly mounted iPod at '/media/IPOD' could not be loaded into gtkpod

And I can do nothing. If I downgrade libgpod to 0.7.0 the iPod will load, but it won't see the songs I save in it. So, any suggestions? 

Thanks

---

