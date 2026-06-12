---
title: "package install"
date: 2010-12-01
forum: General Help
---

### Post by big136 on 2010-12-01
Hi,
on ubuntu 7.1 , I can not install the packages , receiving the followings :




 
 
 
 
user1@ubuntu:~$ rpm -q make-3.80-184.1
The program 'rpm' is currently not installed.  You can install it by typing:
sudo apt-get install rpm
bash: rpm: command not found
user1@ubuntu:~$ sudo apt-get install rpm
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package rpm is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package rpm has no installation candidate
 
Thanks for help.

---

### Post by potat on 2010-12-01
RPM is the package format (and package manager) for Red Hat based distributions. Ubuntu, which is based on Debian, uses .deb format packages. To install a package in Ubuntu...

```

sudo apt-get install <package>

```

Hope this helps.

EDIT: In this case, if you are looking to install make, I suggest the build-essential package. It depends on (and therefore will automagically install) make, as well as other compilation tools.
```

sudo apt-get install build-essential

```

---

### Post by big136 on 2010-12-01
thank you.
But :
user1@ubuntu:~$ sudo apt-get install  gcc-3.3.3-43.24 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gcc-3.3.3-43.24
user1@ubuntu:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package build-essential

---

### Post by WorMzy on 2010-12-01
7.10 (Gutsy Gibbon) is no longer supported and it will be difficult to find packages for it. I recommend that you upgrade to a newer version.

---

### Post by potat on 2010-12-03
Does 7.1 have the GUI distribution upgrade tool? If not, use
```

sudo apt-get dist-updgrade

```

This should upgrade you to 8.04 (Hardy), which is LTS (long-term support) and will be supported till mid-2011. I recommend upgrading at least to the current LTS version, 10.04, if possible. Hope this helps.

---

