---
title: "Removing unwanted packages"
date: 2010-08-14
forum: General Help
---

### Post by lwalper on 2010-08-14
Noob here ...

I recently installed Apache2, PHP, and MySql - everything seemed to run as designed. So now, I'm reading more about managing Ubuntu and came across the command

sudo apt-get autoremove

which is purported to remove any packages that were automatically installed but no longer required. I ran the command and noted that everything removed seemed to be related to the recently installed Apache install. Was that a "bad thing", or did I just clean out a cache of temporary files used for the installation. Seems like it was about 54Mb deleted. Am I going to need to reinstall the Apache server software?

At the installation I created a php test file which does seem to run when I enter [http://localhost](http://localhost) in my browser. Maybe everything is working OK??

---

### Post by yabbadabbadont on 2010-08-14
You should be fine.  The autoremove command shouldn't have removed anything that was depended upon by anything you explicitly installed (and still have installed).

---

### Post by lwalper on 2010-08-15
Whew, I was sweating there for a bit.

Thanks!

---

### Post by linux18 on 2010-08-15
mark the thread as solved....
also, get deborphan, it removes unnecessary libraries  
to use just install and type:
sudo apt-get purge $(deborphan)

---

