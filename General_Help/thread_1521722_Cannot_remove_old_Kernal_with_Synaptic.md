---
title: "Cannot remove old Kernal with Synaptic"
date: 2010-07-01
forum: General Help
---

### Post by schwabdale on 2010-07-01
Hello,
I installed 2.6.34 and no longer need 2.6.32-21. 
When I go into the package manager and mark it for removal...It looks like it tries to install 2.6.32-22 and 2.6.32-22 Generic and then upgrade Linux-headers-generic. 

Can someone give me some direction?

---

### Post by schwabdale on 2010-07-13
Any advice on this? It seems like there is a problem when downloading the new kernal, it errors out.

---

### Post by snowpine on 2010-07-13
You can remove the "linux-image-generic" and "linux-headers-generic" metapackages if you want full manual control over kernel installation and updates. 

I should point out however that there is no benefit to removing the old kernel (other than a small amount of drive space) and in fact it might be helpful to have a 2.6.32 kernel as a fall-back if you ever need to troubleshoot the 2.6.34 kernel you installed yourself.

---

### Post by schwabdale on 2010-07-14
Thanks!

---

### Post by bobcollard on 2010-07-14
If it is no longer useful, sometimes it can be removed using either of the following commands in Terminal:
```
sudo aptitude dist-upgrade
```
```
sudo apt-get autoremove
```

---

