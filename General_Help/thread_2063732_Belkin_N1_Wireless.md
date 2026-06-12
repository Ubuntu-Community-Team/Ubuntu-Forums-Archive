---
title: "Belkin N1 Wireless"
date: 2012-09-27
forum: General Help
---

### Post by Nicosdog on 2012-09-27
I have been given a Belkin N1 wirelss and started following a thread on another forum but still cannot get this to work.

so far I have install ndisgtk then run it - pointed it at netmw245 driver and it comes up saying that I need to ensure that ndiswrapper is installed.

so I am still nowhere and dont really understand what I am doing. Can someone please help me??

---

### Post by ajgreeny on 2012-09-27
I had a similar problem when I tried to use ndiswrapper and ndisgtk on my Lubuntu 12.04 with an old Netgear WG511v2 pcmcia card.  It appears that ndiswrapper and/or ndisgtk in Lubuntu (and probably all the ubuntu family) 12.04 is bugged, and I had to compile it using the source package available in the repos.

The bug is at [https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/986064](https://bugs.launchpad.net/ubuntu/+source/ndiswrapper/+bug/986064) with a few links to other webpages that may be a great help to you.

---

### Post by Nicosdog on 2012-10-26
Hi All

I am still having trouble with ndiswrapper for my N1 Belkin wireless. I have upgraded my Ubuntu to the latest version in hope that it might help but with no luck. I have also tried installing the ndiswrapper-dkms but that caused an error and bug report

Does anyone have any suggestions and easy to follow instructions please?

---

