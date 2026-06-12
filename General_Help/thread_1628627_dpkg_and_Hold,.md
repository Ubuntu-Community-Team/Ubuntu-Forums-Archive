---
title: "dpkg and Hold,"
date: 2010-11-22
forum: General Help
---

### Post by oaxacamatt1 on 2010-11-22
Hi all,
I have a question regarding dpkg and "hold".  

Let me explain. I do not use Gwibber (or whatever it is called) and a few other Ubuntu 10.04 progs.  So I have decided not to delete the progs because I have noticed that one can 'break' things. Instead I would like to use:

"dpkg -hold package_name_I_dont_want.deb"

For the packages I don't want and don't need updated.

What do people think about this approach?  Is there a better way?
Cheers,
M

---

### Post by dcstar on 2010-11-23
> **oaxacamatt1 said:**
> Hi all,
I have a question regarding dpkg and "hold".  

Let me explain. I do not use Gwibber (or whatever it is called) and a few other Ubuntu 10.04 progs.  So I have decided not to delete the progs because I have noticed that one can 'break' things. Instead I would like to use:

"dpkg -hold package_name_I_dont_want.deb"

For the packages I don't want and don't need updated.

What do people think about this approach?  Is there a better way?
Cheers,
M

Just use Synaptic to "Pin" any package to its current version - these GUI tools exist so people don't have to stuff around with the command line.

---

### Post by oaxacamatt1 on 2010-11-23
Hi Dcstar,
Thanks for the idea.  I found that synaptic does not use the actual term 'PIN' but does allow you to 'LOCK' the version that you have.  I have tried that and believe that should do the job.
Cheers,
M

---

### Post by oldos2er on 2010-11-23
Uninstalling Gwibber shouldn't break anything.

---

