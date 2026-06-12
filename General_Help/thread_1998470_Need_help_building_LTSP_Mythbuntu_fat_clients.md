---
title: "Need help building LTSP Mythbuntu fat clients"
date: 2012-06-06
forum: General Help
---

### Post by rage_311 on 2012-06-06
I'm attempting to build a 64-bit Mythbuntu 12.04 LTSP fat client from a 64-bit 10.04.3 Ubuntu server and having no luck.

Using ltsp-server 5.2.1-0ubuntu9:

If I go straight for the 12.04 Mythbuntu client using:
```
sudo ltsp-build-client --purge-chroot --arch amd64 --dist precise --mythbuntu --mythbuntu-user-credentials="mythuser:password"
```
It fails, stating that the mythuser can't be added to the admin group -- apparently it doesn't exist in 12.04.
See:
[HTML]http://ubuntuforums.org/showthread.php?p=11981122[/HTML]
[HTML]https://bugs.launchpad.net/ubuntu/+source/ltsp/+bug/1007565[/HTML]
The official response is that the mythbuntu portion of ltsp-build-client was unmaintained and removed.  So, it won't work for a 12.04 client.


If I try to install a straight 12.04 Ubuntu or Xubuntu fat client (with the intention of installing mythbuntu-desktop packages on top of it) using:
```
sudo ltsp-build-client --purge-chroot --dist precise --fat-client --fat-client-desktop ubuntu-desktop
```
The client fails to boot, stating that it couldn't find the kernel image: vmlinuz.


If I try to install a 10.04 Ubuntu/Xubuntu fat client, with the painful intention of upgrading to 12.04 and installing the mythbuntu-desktop, using:
```
sudo ltsp-build-client --purge-chroot --fat-client --fat-client-desktop xubuntu-desktop
```
The client boots up in thin client mode...  and I'm struggling to figure out why...


Am I missing something?  Is there a better way?  I have been struggling with this for 2 weeks now (and on and off for several months) and could really use some help.  Thanks in advance.

---

