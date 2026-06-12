---
title: "Problems installing Drupal"
date: 2011-12-13
forum: General Help
---

### Post by tech291083 on 2011-12-13
Hi,
I am trying to install Drupal but this is what I get in a terminal. Mine is Ubuntu 10.04 version. Please help me, thanks.

```

root@james-desktop:~# sudo apt-get install drupal7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package drupal7
root@james-desktop:~# sudo apt-get install drupal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package drupal

```

---

### Post by maverickaddicted on 2011-12-13
Have you added the Drupal repository, if not then choose the closet mirror to you from here and add it in your -

[http://packages.debian.org/sid/all/drupal7/download](http://packages.debian.org/sid/all/drupal7/download)

after that try to install Drupal.

It works for me.

---

### Post by leg on 2011-12-13
Personally I wouldn't install through the package manager. Get the latest version from [Drupal.org]("http://drupal.org/download") and uncompress it to your var/www folder. Create a DB and run the install script.

---

### Post by gordintoronto on 2011-12-13
If you run Synaptic Package Manager and search for Drupal, you will see why you got those errors. 

As Leg pointed out, even the latest version of Ubuntu still has Drupal6 in its repositories, while 7.10 is available at drupal.org.

---

