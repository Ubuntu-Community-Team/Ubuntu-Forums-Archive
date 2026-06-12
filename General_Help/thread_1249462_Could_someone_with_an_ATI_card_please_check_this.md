---
title: "Could someone with an ATI card please check this"
date: 2009-08-25
forum: General Help
---

### Post by Stevie78 on 2009-08-25
PROBLEM SOLVED : SEE BELOW




Hi all,

My problem is in this post:

[http://ubuntuforums.org/showthread.php?t=1156640](http://ubuntuforums.org/showthread.php?t=1156640)  

I have purged the file

**fglrx-amdcccle**

via root. There was another 'bad' file that I installed though and as far as I remember fglrx-amdcccle was the one that depended on the other.

Which one was it though?

Could someone with an ATI card who has not changed any default driver yet please check in Synaptic which file fglrx-amdcccle depends on... Thanks.

---

### Post by uylug on 2009-08-25
> **Stevie78 said:**
> Hi all,

My problem is in this post:

[http://ubuntuforums.org/showthread.php?t=1156640](http://ubuntuforums.org/showthread.php?t=1156640)  

I have purged the file

**fglrx-amdcccle**

via root. There was another 'bad' file that I installed though and as far as I remember fglrx-amdcccle was the one that depended on the other.

Which one was it though?

Could someone with an ATI card who has not changed any default driver yet please check in Synaptic which file fglrx-amdcccle depends on... Thanks.
Does this help?

```
$ sudo apt-get install fglrx-amdcccle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  dkms fakeroot fglrx-kernel-source lib32gcc1 libc6-i386 patch
  xorg-driver-fglrx
Suggested packages:
  diff-doc libamdxvba1
The following NEW packages will be installed:
  dkms fakeroot fglrx-amdcccle fglrx-kernel-source lib32gcc1 libc6-i386 patch
  xorg-driver-fglrx
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 36.1MB/36.3MB of archives.
After this operation, 108MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

I've got an ATI X550 running Jaunty

---

### Post by Stevie78 on 2009-08-25
YES IT HELPED !!

I also purged **xorg-driver-fglrx** and my desktop is back to normal :):)

Thanks a lot!

---

### Post by uylug on 2009-08-25
Sweet! Glad to help! Thanks for posting after your issue had been solved! Some people don't do that!

---

