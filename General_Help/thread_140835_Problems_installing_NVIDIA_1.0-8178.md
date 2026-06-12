---
title: "Problems installing NVIDIA 1.0-8178"
date: 2006-03-07
forum: General Help
---

### Post by QuacoreZX on 2006-03-07
Well, I've been going by the guide from the wiki for installing a downloaded NVIDIA installer.  I started out by deleting the former nvidia components installed via apt-get and log files associated with it, set CC=gcc-3.4 and exported in both root and user, stopped gdm, then started the installer.  

Unfortunately, it seems setting CC=3.4 wasn't such a good idea since my kernel was appearantly compiled with gcc4.0.  

So I exited out of the installer, set CC=gcc-4.0 and exported, and tried again, but now it recognized that I didn't even have a compiler set!  I exited out again and set CC=/usr/bin/gcc-4.0 and exported and tried again, once again to the same result!

Question here is: how do I set my default gcc compiler to gcc-4.0?

---

### Post by Xian on 2006-03-07
Frist try this command:

```
$ sudo export CC=/usr/bin/gcc-4.0
```

Which gcc version are you using?

```
$ ls -l /usr/bin/gcc* /usr/bin/cpp* /usr/bin/g++*
```

It should look similar to this:

```
lrwxrwxrwx 1 root root     7 2006-03-05 05:58 /usr/bin/cpp -> cpp-4.0
-rwxr-xr-x 1 root root 97136 2006-03-04 23:04 /usr/bin/cpp-4.0
lrwxrwxrwx 1 root root     7 2006-03-05 05:58 /usr/bin/g++ -> g++-4.0
-rwxr-xr-x 1 root root 97136 2006-03-04 23:05 /usr/bin/g++-4.0
lrwxrwxrwx 1 root root     7 2006-03-05 05:58 /usr/bin/gcc -> gcc-4.0
-rwxr-xr-x 1 root root 93648 2006-03-04 23:07 /usr/bin/gcc-4.0
lrwxrwxrwx 1 root root    10 2006-03-05 05:58 /usr/bin/gccbug -> gccbug-4.0
-rwxr-xr-x 1 root root 16268 2006-03-04 22:59 /usr/bin/gccbug-4.0
```

If not then make the proper symlinks:

```
$ sudo rm /usr/bin/gcc
$ sudo ln -s /usr/bin/gcc-4.0 /usr/bin/gcc
```

And do the same for cpp and g++

---

### Post by SWAT on 2006-03-07
[Have a look at my HowTo](http://www.zwhlug.nl/content/nvidia_nvidia_driver_1_0_8178_installation_on_ubuntu_breezy_5_10). I'm currently using those drivers (and they work like a charm :D

---

