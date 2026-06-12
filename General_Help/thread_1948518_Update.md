---
title: "Update"
date: 2012-03-28
forum: General Help
---

### Post by hallo200 on 2012-03-28
Hallo Forum,

how can I do security updates in ubuntu on the command line? Is it done with:
"apt-get upgrade"?

But this installes new versions of packages. The config files of the packages eventually do not fit with the new version. Also Nvidia driver cause problems after a kernel update. Normally it is a must to install update but we have 40 Clients. I cannot do upgrades and invest 2 hours per machine for fix broken config files and packages.

Thanks for your opinion and
with kind regards
hallo200

---

### Post by hallo200 on 2012-03-29
Is there no opinion of a experienced Ubuntu Guy?

regards
hallo 200

---

### Post by raja.genupula on 2012-03-29
> **hallo200 said:**
> Hallo Forum,

how can I do security updates in ubuntu on the command line? Is it done with:
"apt-get upgrade"?

But this installes new versions of packages. The config files of the packages eventually do not fit with the new version. Also Nvidia driver cause problems after a kernel update. Normally it is a must to install update but we have 40 Clients. I cannot do upgrades and invest 2 hours per machine for fix broken config files and packages.

Thanks for your opinion and
with kind regards
hallo200

yes security updates you can get with that ,if you check security updates check box in the settings of the update manager , 

Actually some times after kernel upgrades we need to install graphics drivers . but i heard there is some packages which will auto update the graphics drivers also after kernel upgrades .

so i hope this will help you on this 
[http://ubuntuforums.org/showthread.php?t=835573](http://ubuntuforums.org/showthread.php?t=835573)

---

### Post by sudodus on 2012-03-29
I have not used it but found ***--no-install-recommends*** in ```
man apt-get
```

So I suggest that you try
```
sudo apt-get update
```
```
sudo apt-get upgrade --no-install-recommends
```
Good luck and please let us know your result :-)

---

