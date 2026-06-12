---
title: "kernel updates and kernel-ppa"
date: 2011-07-15
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-07-15
[http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu](http://ppa.launchpad.net/kernel-ppa/ppa/ubuntu)
so i added that ppa so i could get trim support in lucid (currently using 2.6.35-25 (if i this kernel is no longer receiving updates let me know))
and i just gt a security update for the 2.6.32-33 kernel
how can i have it not offer to update the old kernel anymore
edit locked stuff in synaptic (linux generic/linux image generic)

---

### Post by SlugSlug on 2011-07-15
remove the old kernel
either with apt-get or use ubuntu tweak there is clean up section in there

---

### Post by Ad@m on 2011-07-15
If you do not wish to remove the kernel but prevent it from being updated,

```
sudo apt-get install wajig

dpkg --get-selections | grep linux
```You will now see a list of kernel packages installed on your system. Set the ones you wish to exclude from an upgrade / update on hold.

```
sudo wajig hold packagename
```For example,

sudo wajig hold linux-image-2.6.38-10-generic

Now if you run **dpkg --get-selections | grep linux **again,

you will see its status has changed to hold.

---

### Post by ajgreeny on 2011-07-15
I've not come across the wajig package before, but it is also possible to pin any package to the current version very easily with no extra additions to your system.

To pin a package version add these lines to  /etc/apt/preferences:
```
Package: name                
Pin: version *(current number from repos)*    
Pin-Priority: 1001
```

---

