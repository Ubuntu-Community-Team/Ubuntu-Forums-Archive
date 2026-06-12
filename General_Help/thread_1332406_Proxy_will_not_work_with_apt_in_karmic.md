---
title: "Proxy will not work with apt in karmic"
date: 2009-11-20
forum: General Help
---

### Post by beattyml1 on 2009-11-20
When I first booted my new 32 bit karmic install I found that the proxy settings worked for konquerer but not for apt.   I was able to download the packages manually from the repo using konquerer and one of the provided mirrors.

I had the same issue with the 32 bit kubuntu karmic release candidate. 

I did not have these issues with 64-bit Ubuntu jaunty install running a kde session.

I have currently fallen back on my old jaunty install, but still have my new kubuntu karmic install and just need to do MBR change to get back.

---

### Post by nxt on 2009-11-24
you must export your proxy settings within the shell

http_proxy="http://username:password@proxyserver:proxyport"
export http_proxy


to make this permament I suggest adding these line either to
/etc/bash.bashrc or to ~/.profile file

---

### Post by lalamax3d on 2010-01-13
writing file to /etc/bash.bashrc and then logout, login, opening konsole gives error about wrong command.

any ideas??

whats difference in writing between bash.bashrc or .profile file.
bash.bashrc is systemwide setting and .profile is user based?? correct??

---

