---
title: "How to install AS400 client (iSeriesAccess) in ubuntu 10.04"
date: 2010-07-19
forum: General Help
---

### Post by dilantha on 2010-07-19
Hi Everyone,

Im trying to install iSeriesAccess in ubuntu 10.04. I have found some articles in installing iSeriesAccess in older versions in ubuntu. but unfortunately those steps did not work with 10.04. this is the article that i have followed

[http://ubuntuforums.org/showthread.php?t=165337](http://ubuntuforums.org/showthread.php?t=165337)

after following all the steps when i tried to launch the program it gave me the following error  

```
error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```Then i found that there is no libstdc++.so.5 file inside /usr/local/lib/ folder. but there is a libstdc++.so.6 file inside /usr/lib/ folder. so i created a symlink to that by using libstdc++.so.5n name.

```
ln -s /usr/lib/libstdc++.so.6 /usr/lib/libstdc++.so.5
```now im getting this error

```
/opt/ibm/iSeriesAccess/bin/ibm5250: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by /opt/ibm/iSeriesAccess/bin/ibm5250)
/opt/ibm/iSeriesAccess/bin/ibm5250: /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by /opt/ibm/iSeriesAccess/bin/ibm5250)
/opt/ibm/iSeriesAccess/bin/ibm5250: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2.2' not found (required by /usr/lib/libcwbcore.so)
/opt/ibm/iSeriesAccess/bin/ibm5250: /usr/lib/libstdc++.so.5: version `CXXABI_1.2' not found (required by /usr/lib/libcwbcore.so)
/opt/ibm/iSeriesAccess/bin/ibm5250: /usr/lib/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by /usr/lib/libcwbcore.so)
```Can someone help me in this issue?
Thanks..

---

### Post by mozart_ar on 2010-07-20
maybe you are trying to install on ubuntu 64, then see this

[IBM iSeries Client Access in Ubuntu 10.04 LTS](http://n8.thruhere.net/blog/?p=142)

---

### Post by dilantha on 2010-07-21
> **mozart_ar said:**
> maybe you are trying to install on ubuntu 64, then see this

[IBM iSeries Client Access in Ubuntu 10.04 LTS]("http://n8.thruhere.net/blog/?p=142")

Hi mozart_ar,

Thanks a lot for the link. Now it is working fine. :D:D

---

### Post by n8bounds on 2011-05-10
[SIZE="4"]Updated for Natty: [http://n8.thruhere.net/blog/?p=1122]("http://n8.thruhere.net/blog/?p=1122")[/SIZE]

---

