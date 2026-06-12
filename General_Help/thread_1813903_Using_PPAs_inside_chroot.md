---
title: "Using PPAs inside chroot ?"
date: 2011-07-28
forum: General Help
---

### Post by linuxyogi on 2011-07-28
Hi,

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

> A chroot is basically a special directory on your computer which  prevents applications, if run from inside that directory, from accessing  files outside the directory. In many ways, a chroot is like installing  another operating system inside your existing operating system. **Is it somehow possible to configure chroot to allow (read only) access to a**** particular folder outside chroot ?**

If that is possible I will install some useful but untrusted/unofficial PPAs inside the chroot environment. But if it is impossible to configure chroot to allow access to a folder outside there is no point.


> **Accessing graphical applications inside the chroot**

 You  can run graphical applications within a chroot, but you need to provide  an X server for them to run in first. The easiest way to do this is to  set the display of the chroot system to be identical to the root display  of your system's main X server. 
In other words, in the chroot shell type  
export DISPLAY=:0.0But question is will the NVIDIA proprietery driver run inside chroot ? vdpau possible ?

---

### Post by sisco311 on 2011-08-01
> **linuxyogi said:**
> Hi,

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

**Is it somehow possible to configure chroot to allow (read only) access to a**** particular folder outside chroot ?**

If that is possible I will install some useful but untrusted/unofficial PPAs inside the chroot environment. But if it is impossible to configure chroot to allow access to a folder outside there is no point.


Yes, you can mount any partition, directory or file, from outside the chroot environment the same way you mount dev, proc and sys.

```
sudo mount --bind /path/to/source /var/chroot/path/to/dest
```
If you want to make it read-only, you have to issue a second remount command:
```
sudo mount -o remount,ro /var/chroot/path/to/dest
```

---

