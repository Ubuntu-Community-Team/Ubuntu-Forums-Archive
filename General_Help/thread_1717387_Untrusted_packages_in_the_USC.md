---
title: "Untrusted packages in the USC?"
date: 2011-03-29
forum: General Help
---

### Post by vanattab on 2011-03-29
I have just recently installed ubuntu on a new (new to me at least) machine and am have some trouble installing common programs from the USC. Like Amarok, BlueFish.. ect. Pretty much everything I have tried says it requires download from untrustworthy source. All installed fine on my laptop. I am running natty narwahl on this computer and 10.10 on my laptop. The content of my software sources is shown in the image below

Any hints ?

[IMG]http://ampache.dyndns-remote.com/Screenshot.png[/IMG]

---

### Post by oldos2er on 2011-03-29
Open a terminal and run **sudo apt-get update**. When that is done, retry Software Center. If it still isn't working, please post the output from sudo apt-get update, which should show which repositories are causing the problem.

[https://help.ubuntu.com/community/SecureApt](https://help.ubuntu.com/community/SecureApt)

---

