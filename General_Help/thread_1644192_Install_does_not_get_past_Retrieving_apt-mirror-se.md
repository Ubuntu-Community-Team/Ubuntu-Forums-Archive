---
title: "Install does not get past Retrieving apt-mirror-setup"
date: 2010-12-12
forum: General Help
---

### Post by FatsWaler on 2010-12-12
Hi All,

I am trying to install ubuntu studio 10.10 it starts to go through the setup steps but after it scans the cd I get the message "Retrieving apt-mirror-setup" and it stays ay 0%.

I have tried both with internet and without and I get the same problem. It is a brand new disc with no os ever installed on it. Is the a way to force the installer to skip the mirror check?

Thanks

---

### Post by aubster on 2011-03-17
Hi. 

Did you get your problem resolved. I think it might just take a long time to download. 

I have the following problem. 

I do need some help. I am using Ubuntu 10.10 Server. And I can not get
the apt-mirror to work. It can not open the Sources.gz file. You will
notice the URL has a // between ubuntu and dists. I have setup a
repository using Ubuntu 9.10 but the Ubuntu 10.x does not work due to
this problem.

Your help would be appreciated on the matter.

Here is the mirror.list file content:
#
 set base_path    /var/spool/apt-mirror
#
 set mirror_path  $base_path/mirror
 set skel_path    $base_path/skel
 set var_path     $base_path/var
 set cleanscript $var_path/clean.sh
# set defaultarch
# set postmirror_script $var_path/postmirror.sh
# set run_postmirror 0
set nthreads     20
set _tilde 0
#
############# end config ##############
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted universe
multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main restricted
universe multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main restricted
universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-proposed main
restricted universe multiverse
#deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-backports main
restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted
universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-security main
restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-updates main
restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-proposed main
restricted universe multiverse
#deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick-backports main
restricted universe multiverse
clean [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu)

---

### Post by bimmerd00d on 2011-12-13
I ended up having to use a USB flash drive to perform the installation.  Lookup unetbootin.

---

