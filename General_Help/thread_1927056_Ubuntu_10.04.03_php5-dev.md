---
title: "Ubuntu 10.04.03 php5-dev"
date: 2012-02-17
forum: General Help
---

### Post by Linsys on 2012-02-17
Hi,

I am new to Ubuntu coming from a purely RHEL, CentOS and UEL background so I might not understand some differences yet. 

I'm having a problem installing php5-dev using apt-get, here is the error I am receiving

The following packages have unmet dependencies:
  php5-dev: Depends: autoconf (>= 2.63) but it is not installable
            Depends: automake (>= 1.11) but it is not installable
            Depends: libssl-dev but it is not going to be installed
            Depends: libtool (>= 2.2) but it is not installable
            Depends: shtool but it is not installable
E: Broken packages

If I run an apt-get update; apt-cache search libtool I don't even see the libtool package in the list. I am probably missing a repo but I can't seem to figure out what/where. 

Here are the Repos (not sure what they are really called in the Ubuntu world) in my /etc/apt/sources.list
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) lucid-security multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) lucid multiverse
deb [http://mirror.anl.gov/pub/ubuntu/](http://mirror.anl.gov/pub/ubuntu/) lucid universe

Any help would be greatly appreciated.

---

### Post by Linsys on 2012-02-17
Ok I found this tool [http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/) it generated a new sources.list for me and my problems are now all solved.

---

