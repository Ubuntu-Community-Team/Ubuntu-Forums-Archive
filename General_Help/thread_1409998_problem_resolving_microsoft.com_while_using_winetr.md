---
title: "problem resolving microsoft.com while using winetricks"
date: 2010-02-18
forum: General Help
---

### Post by sur_babu on 2010-02-18
Dear all,

I am very very new to linux env, so would appreciate if someone can advise me. I am searching through google for all of my problems, but got stuck in the following.

I am willing to install Office2007 in ubuntu, and have installed wine and winetricks as per the guidelines. Now while running the office cd, xml parser3/vc++ and .Net framework installation is failing.

From winetricks guidelines I am trying to install  dotnet11, dotnet20, gdiplus, msxml3, msxml4, msxml6, vcrun2005sp1 and vcrun2008.. But the only error I am getting is the following. This is uniform across anything I try to install from the above. Why in this world it's not resolving I donno.

 --2010-02-18 19:06:07--  [http://download.microsoft.com/download/6/B/B/6BB661D6-A8AE-4819-B79F-236472F6070C/vcredist_x86.exe](http://download.microsoft.com/download/6/B/B/6BB661D6-A8AE-4819-B79F-236472F6070C/vcredist_x86.exe)
Resolving download.microsoft.com... failed: Name or service not known.
wget: unable to resolve host address `download.microsoft.com'

Please help,

Best,

---

### Post by sur_babu on 2010-02-18
FYI, I just tried installing shockwave player, and it worked fine. Any microsoft thing is failing...

root@surajit:/home/surajit/Desktop# sh winetricks shockwave
Executing wget -O sw_lic_full_installer.msi -nd -c --read-timeout=300 --retry-connrefused --header Accept-Encoding: gzip,deflate [http://fpdownload.macromedia.com/get/shockwave/default/english/win95nt/latest/sw_lic_full_installer.msi](http://fpdownload.macromedia.com/get/shockwave/default/english/win95nt/latest/sw_lic_full_installer.msi)
--2010-02-18 19:18:58--  [http://fpdownload.macromedia.com/get/shockwave/default/english/win95nt/latest/sw_lic_full_installer.msi](http://fpdownload.macromedia.com/get/shockwave/default/english/win95nt/latest/sw_lic_full_installer.msi)
Resolving fpdownload.macromedia.com... 125.252.210.70
Connecting to fpdownload.macromedia.com|125.252.210.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13845504 (13M) [application/x-msi]
Saving to: `sw_lic_full_installer.msi'

Best,

---

### Post by sur_babu on 2010-02-18
NM, for some odd reason the domain name for this particular thing was not getting resolved. Manually put the entry to the etc/hosts and now it's working..

Best,

---

