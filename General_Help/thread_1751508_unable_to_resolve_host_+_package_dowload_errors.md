---
title: "unable to resolve host + package dowload errors"
date: 2011-05-06
forum: General Help
---

### Post by czaravm on 2011-05-06
Hey, I am running 11.04 on a 5,3 MacBook Pro. For the last two days, every time that I attempt to use the sudo command, and subsequently, install packages, I come up with errors.

For instance, trying to install sabnzbdplus:
```
alec@ubuntu:~$ sudo apt-get install sabnzbdplus
sudo: unable to resolve host ubuntu
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sabnzbdplus is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up bcm5974-dkms (1.1.4) ...
Loading new bcm5974-1.1.4 DKMS files...

Error! Cannot locate /usr/src/bcm5974-1.1.4.dkms.tar.gz.
File does not exist.
dpkg: error processing bcm5974-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcm5974-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)
alec@ubuntu:~$ 

```

As you can see I have the "unable to resolve host HOSTNAME" error, which I tried to remedy using help from this forum, but my /etc/hosts file is absolutely normal: 


```
alec@ubuntu:~$ more /etc/hosts
127.0.0.1	localhost
127.0.1.1	ubuntu

# The following lines are desirable for IPv6 capable hosts
::1     localhost ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```

In addition, (I am assuming this is just dependant on the fact that I can't use sudo, but maybe it will help you guys) I get the error message:

```
Errors were encountered while processing:
 bcm5974-dkms

```

This is supposedly due to the dkms tarball being unfindable.

I would really love to get back to normal usage of my desktop, and any help would be great! THANKS!

---

