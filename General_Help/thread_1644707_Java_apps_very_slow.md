---
title: "Java apps very slow"
date: 2010-12-13
forum: General Help
---

### Post by bluebelle on 2010-12-13
I am running Ubuntu 10.04 desktop, 64bit and some of the apps I use are Zend Studio (PHP development suite) and VirtualBox. Most of the time they run fine, but occasionally Zend studio starts choking as it tries to process a particularly long file. By "particularly long" I mean about 1000-2000 lines of code, something that Dreamweaver running in a Windows guest virtual machine processes and colours just fine, on the same physical box. Aside from that, VirtualBox itself occasionally goes into a state of consuming 40% of my CPU constantly and renders the system almost unusable. 

More recently, I was opening a 1MB sized PDF file and there too the default app started choking on it, and then crashed, taking with it my Zend Studio, VirtualBox and even Firefox instances.

Am I missing something? I am using whatever Java environment came with Ubuntu, the applications I use come either from Ubuntu's repositories or, in case of Zend and VirtualBox, from makers' websites. Does anyone else have problems with Java applications on Ubuntu, is there something I can do to improve things?

---

### Post by lykeion on 2010-12-14
This does not sound like a Java problem. VirtualBox is written in C/C++ and Evince (PDF reader) in C. I'm not sure about Zend Studio; the homepage says nothing of any Java requirements.
To me it sounds more like swap/memory problems. How much RAM does your computer have?

---

### Post by bluebelle on 2010-12-14
Zend Studio is based on Eclipse, which is java based. Not sure if they use system provided java libraries or their own. 

It did seem kind of fun the way so many applications just crashed at once. Oh well, at least the Terminal kept running. :)

My computer has 4GB of RAM, running on 2GHz core2duo. You'd think this should be enough for anyone ;).

> **lykeion said:**
> This does not sound like a Java problem. VirtualBox is written in C/C++ and Evince (PDF reader) in C. I'm not sure about Zend Studio; the homepage says nothing of any Java requirements.
To me it sounds more like swap/memory problems. How much RAM does your computer have?

---

### Post by lykeion on 2010-12-14
Yes 4GB RAM should be plenty.

Really hard to troubleshoot this. I suggest you to search in this forum or google your problem with keywords like "ubuntu" "high cpu usage" "core2duo", and maybe adding the name(s) of the application(s) that cause the crash. This link came up when I searched (don't know if it helps you): [How To Fix VirtualBox High CPU Load with Ubuntu 9.10 Host](http://r3dux.org/2009/11/how-to-fix-virtualbox-high-cpu-load-with-ubuntu-9-10-host/)

Otherwise you could search [Launchpad]("https://launchpad.net/ubuntu"). Check [ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) before you file any bugs to Launchpad.

---

### Post by bluebelle on 2010-12-14
Thanks for suggestions, will check them out.

---

