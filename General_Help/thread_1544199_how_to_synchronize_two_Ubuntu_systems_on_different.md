---
title: "how to synchronize two Ubuntu systems on different machines"
date: 2010-08-02
forum: General Help
---

### Post by ubmwu2649 on 2010-08-02
I installed Ubuntu 10.4 on my PC in the office and I also installed it on my home PC.  From time to time, I install additional programs or change configuration on the Ubuntu system I work on.  It makes my working environments on these two Ubuntu systems different from each other.

Can some ones give me an advice on working practices to synchronize two Ubuntu systems?  Is there any program or utility I can use to accomplish the goal?

Thanks in advance!
Michael Wu

---

### Post by ubmwu2649 on 2010-08-04
At last, I found a solution which serves my need.  With it, I need not to synchronize because I actually use the same Ubuntu system either at home or in the office.

I use VirtualBox software.  Install it on Windows 7 at home.  Install another on the Ubuntu system in the office.  I then install another Ubuntu system with one of the VirtualBox instances.  The last Ubuntu system is contained in a vdi file.  It is the file I bring to the office or bring back to my home.  When I am working in the office, I start the VirtualBox on the office PC which run Ubuntu system.  After that, the Ubuntu client system is started.  Right.  An ubuntu system exists in another ubuntu system.  Similarly, I start the VirtualBox on the home PC which runs Windows 7.

With this approach, I can carry my actual working Ubuntu system with me.  I only need to carry the disk which contains my vdi file.

---

