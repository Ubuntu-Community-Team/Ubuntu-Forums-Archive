---
title: "I broke apt-get :("
date: 2010-11-27
forum: General Help
---

### Post by Monotoko on 2010-11-27
Hi guys,

After over 600 posts here...you'd think I would not be making these mistakes anymore, hehe.

Anyway, this time round I appear to have really screwed over apt-get on my (live!) server environment. Luckily the packages on there still work, so my users have noticed nothing different.

But I could do to get this fixed:
```
root@chatify:/home/daniel# apt-get remove vsftpd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 webmin : Depends: libnet-ssleay-perl but it is not going to be installed
          Depends: libauthen-pam-perl but it is not going to be installed
          Depends: libio-pty-perl but it is not going to be installed
          Depends: apt-show-versions but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

As you can see, I attempted to install webmin which went horribly. But it gives me an option to get rid of the error, so I use it:

```
root@chatify:/home/daniel# apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  apt-show-versions libauthen-pam-perl libio-pty-perl libnet-ssleay-perl
The following packages will be REMOVED
  vsftpd
The following NEW packages will be installed
  apt-show-versions libauthen-pam-perl libio-pty-perl libnet-ssleay-perl
0 upgraded, 4 newly installed, 1 to remove and 19 not upgraded.
2 not fully installed or removed.
Need to get 0B/319kB of archives.
After this operation, 1,085kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 36114 files and directories currently installed.)
Removing vsftpd ...
dpkg: error processing vsftpd (--remove):
 subprocess installed post-removal script returned error exit status 1
Processing triggers for ureadahead ...
Errors were encountered while processing:
 vsftpd
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So I'm a bit stuck, how can I make dpkg work again?

Daniel

---

### Post by oldos2er on 2010-11-27
Which version of Ubuntu are you using? Do you have the universe repository enabled? Check in Synaptic Package Manager, Settings, Repositories.

---

### Post by Monotoko on 2010-11-27
I'm using Ubuntu 10.10 but I managed to sort it using this: [http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html](http://www.cyberciti.biz/tips/troubleshooting-debian-ubuntu-package-upgrades-removals.html)

I removed the "set -e" from all of the vsftpd related files and it went through :)

---

### Post by oldos2er on 2010-11-27
Glad you solved it.

---

