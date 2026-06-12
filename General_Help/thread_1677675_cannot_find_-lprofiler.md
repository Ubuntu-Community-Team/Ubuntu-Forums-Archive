---
title: "cannot find -lprofiler"
date: 2011-01-29
forum: General Help
---

### Post by jiapei100 on 2011-01-29
Hi, all:

I'm trying to install gazebo and during the installation process, it complains that 
> cannot find -lprofiler

Sorry but can anybody help to explain 
1) what is lprofile ?
2) which package should I install for this lprofile?

Thank you very much.

Best Regards
JIA

---

### Post by TheHackOps on 2011-01-29
As far as i can tell lprofiler is not a default library, i will try to find and install the package you were trying and report back my findings


Edit:
I found this if you didn't follow it

[http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/install.html](http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/install.html)

---

### Post by jiapei100 on 2011-01-29
Thank you for your prompt reply.

I fount it. I may have to install
> libgoogle-perftools-dev

After having installed this package, there is a library named libprofile.a installed .


Thanks anyway.

Best Regards
JIA



> **TheHackOps said:**
> As far as i can tell lprofiler is not a default library, i will try to find and install the package you were trying and report back my findings


Edit:
I found this if you didn't follow it

[http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/install.html](http://playerstage.sourceforge.net/doc/Gazebo-manual-0.5-html/install.html)

---

