---
title: "compiling or installing apps"
date: 2010-06-30
forum: General Help
---

### Post by caspah on 2010-06-30
1 - Installing...  seems unless the app is pre-setup for Ubuntu you need to compile it, assign permissions, and then install.  Is there an easier way to do this?  Like a app that does this for you?

Sorry to sound lazy but I haven't used *nix commands in years.

2 - Drivers..  Seems the only driver I have access too is the video driver.  Ubuntu had no problem finding drivers for my mini fuji smartbook u810 with its 40+ gadgets.  But when I installed it on my alienware laptop m17 there seems to be a bunch missing.  

Is there a more in-depth driver app?  For say like a razor deathadder 3500 gaming mouse?

thanx

---

### Post by warfacegod on 2010-06-30
This may be useful for question 01. [http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)

---

### Post by iponeverything on 2010-06-30
what version are you trying to install?

Generally compiling is pretty painless.

the "make install" takes care of details like permissions and ownership. 

many compiles are as simple as:

```

./configure
make 
make install

```

Though it always good to look instructions, usually located at the top level of the archive.

---

### Post by gordintoronto on 2010-06-30
Many, many applications are available by using Administration/Synaptic. "Install" takes a couple of mouse clicks.

---

