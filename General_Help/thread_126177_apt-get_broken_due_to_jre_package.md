---
title: "apt-get broken due to jre package"
date: 2006-02-05
forum: General Help
---

### Post by pyromania on 2006-02-05
Hi, I've been trying to install the newest version of Java to run Azureus at the best performance. I failed at the fakeroot with the self-extracting .bin route, so I said screw it and went to install wine via apt-get. When I went to install i got this error.


pyromania@c0k3:~$ sudo apt-get install wine
Reading package lists... Done
Building dependency tree... Done
E: The package jre needs to be reinstalled, but I can't find an archive for it.

I searched some other threads and tried these commands already.

sudo apt-get -f install
sudo apt-get -md install jre
sudo apt-get --purge --force-yes remove jre

All of them gave the error E: The package jre needs to be reinstalled, but I can't find an archive for it.

Thanks in advance for help

---

### Post by jasmuz on 2006-02-06
My recommendation would be that you modify your sources.list and check what repositories you have enabled, add some "non-free" repos where JRE is located and proceed with updating the list, later installing java.

---

### Post by bhartman35 on 2006-05-29
[QUOTE=jasmuz]My recommendation would be that you modify your sources.list and check what repositories you have enabled, add some "non-free" repos where JRE is located and proceed with updating the list, later installing java.[/QUOTE]

Hi, Everyone.

I'm new to the forum, and I'm having the same problem.  Can anyone point me towards a JRE repository so I can get through this?  *Nothing* will install or uninstall for me now, whether I use apt-get or a graphical interface.

Brian

---

