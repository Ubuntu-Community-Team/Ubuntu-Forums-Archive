---
title: "Apt-mirror error (Sources.gz not Found)"
date: 2011-03-17
forum: General Help
---

### Post by aubster on 2011-03-17
Hi. 
  
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

