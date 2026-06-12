---
title: "Broken mirror with apt-mirror"
date: 2012-09-12
forum: General Help
---

### Post by maxxer on 2012-09-12
Hi.
I'm using apt-mirror to create a local ubuntu mirror. We run it nightly, but we have a problem because the mirror is often not consistent.
i.e. when I try to install a new machine using netinstall or pxe I get an error saying package X md5 is wrong.

I checked apt-mirror log and apparently there's no error:
> Downloading 332 index files using 20 threads...
Begin time: Tue Sep 11 22:11:03 2012
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Tue Sep 11 22:14:28 2012

Proceed indexes: [PPPPPPPPPPPPPPPPPPPPPPPPPP]

1.2 GiB will be downloaded into archive.
Downloading 513 archive files using 20 threads...
Begin time: Tue Sep 11 22:31:04 2012
[20]... [19]... [18]... [17]... [16]... [15]... [14]... [13]... [12]... [11]... [10]... [9]... [8]... [7]... [6]... [5]... [4]... [3]... [2]... [1]... [0]... 
End time: Wed Sep 12 02:55:06 2012

839.9 MiB in 310 files and 0 directories can be freed.
Run /var/spool/apt-mirror/var/clean.sh for this purpose.

Running the Post Mirror script ...
(/var/spool/apt-mirror/var/postmirror.sh)


Post Mirror script has completed. See above output for any possible errors.



The LTS mirror config:
```
####### UBUNTU 12.04 
deb http://it.archive.ubuntu.com/ubuntu precise main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu precise-updates main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu precise-security main restricted universe multiverse
deb http://it.archive.ubuntu.com/ubuntu precise-proposed main restricted universe multiverse
# Per NetInst
deb http://it.archive.ubuntu.com/ubuntu precise main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer

deb-i386 http://it.archive.ubuntu.com/ubuntu precise main restricted universe multiverse
deb-i386 http://it.archive.ubuntu.com/ubuntu precise-updates main restricted universe multiverse
deb-i386 http://it.archive.ubuntu.com/ubuntu precise-backports main restricted universe multiverse
deb-i386 http://it.archive.ubuntu.com/ubuntu precise-security main restricted universe multiverse
deb-i386 http://it.archive.ubuntu.com/ubuntu precise-proposed main restricted universe multiverse
# Per NetInst
deb-i386 http://it.archive.ubuntu.com/ubuntu precise main/debian-installer restricted/debian-installer universe/debian-installer multiverse/debian-installer

```


Why do I get broken packages?
thanks

---

### Post by nothingspecial on 2012-09-12
*Thread moved to **General Help**.*

---

