---
title: "Warnings when removing old kernels"
date: 2010-02-10
forum: General Help
---

### Post by HotForLinux on 2010-02-10
After removing old kernels, many files associated with them are lstill eft on the system occupying disk space.

For each old kernel version I wanted to remove, I removed 5 packages :
 
linux-image-2.6.24-21-generic
linux-restricted-modules-2.6.24-21-generic
linux-ubuntu-modules-2.6.24-21-generic
linux-headers-2.6.24-21
linux-headers-2.6.24-21-generic

But the removal and purge of these packages, using the ***aptitude purge*** command, displayed several warnings. For _example_:

a)
```
dpkg - warning: while removing linux-ubuntu-modules-2.6.24-16-generic, directory `/lib/firmware/2.6.24-16-generic' not empty so not removed.
```b)
```
rmdir: failed to remove `/lib/modules/2.6.24-19-generic': Directory not empty
dpkg - warning: while removing linux-image-2.6.24-19-generic, directory `/lib/modules/2.6.24-19-generic/kernel/drivers/input/misc' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.24-19-generic, directory `/lib/modules/2.6.24-19-generic/kernel/drivers/input' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.24-19-generic, directory `/lib/modules/2.6.24-19-generic/kernel/drivers' not empty so not removed.
dpkg - warning: while removing linux-image-2.6.24-19-generic, directory `/lib/modules/2.6.24-19-generic/kernel' not empty so not removed.
dpkg - warning: while removing linux-headers-2.6.24-19-generic, directory `/lib/modules/2.6.24-19-generic' not empty so not removed.
```Moreover, ***deborphan*** shows the following dependencies associated with these packages:

```
linux-headers-2.6.24-22
      dkms
      linux-headers-2.6.24-22-generic
linux-headers-2.6.24-23
      dkms
      linux-headers-2.6.24-23-generic
etc.

linux-headers-2.6.24-24-generic
      dkms
linux-headers-2.6.24-21-generic
      dkms
etc.

linux-image-2.6.24-24-generic
      dkms
      linux-restricted-modules-2.6.24-24-generic
      linux-ubuntu-modules-2.6.24-24-generic
linux-image-2.6.24-21-generic
      dkms
      linux-restricted-modules-2.6.24-21-generic
      linux-ubuntu-modules-2.6.24-21-generic
etc.
```1.
Should I delete all these files and directories, named in the warnings, by hand?:
/lib/firmware/2.6.24-16-generic/
/lib/modules/2.6.24-16-generic/

2.
Also, I located these other directories in the filesystem:

/usr/src/linux-headers-2.6.24-16/
/var/lib/dkms/lirc/0.8.3~pre1/2.6.24-16-generic/

Should I delete these directories too?

3.
I think something should be done to make all these clearer and easier to handle.

---

### Post by aryan22 on 2010-02-10
Removing Directories doesn't really sound like a good idea.
so, first we need to know your current kernel version.
```
uname -r
```
we are gonna remove all kernels except the one in the output
then, we need to find all the older versions.
so type
```
ls /boot | grep vmlinuz | cut -d'-' -f2,3
```
then all you need to do is
```
sudo apt-get remove --purge 2.6.24-16-*
```
change 2.6.24-16- with the kernel version number you wish to remove

---

### Post by HotForLinux on 2010-02-10
>  ```
 ......
sudo apt-get [COLOR=Red]**remove** --purge[/COLOR] 2.6.24-16-*
```change 2.6.24-16- with the kernel version number you wish to removeIf you read.... My post and questions obviously come after reading, knowing and having done all that.

---

### Post by HotForLinux on 2010-02-10
What I think is that if some of the files in those old kernel packages are still needed by installed packages and system work, then something must be wrong when the system allows and tries to remove the old kernel packages. If not then they should be removed COMPLETELY.
I found a post somewhere else in the Internet talking about this issue as a bug.

---

### Post by HotForLinux on 2010-02-11
Bump

---

