---
title: "Network problem with apt"
date: 2006-03-18
forum: General Help
---

### Post by Jeff Eklund on 2006-03-18
Hi!
I'm having a problem with apt since yeasterday. I brought my laptop to my school and connected it to the school network which uses a proxy server to connect to the internet. I also tried setting Synaptic to use a proxy to be able to perform my daily apt-get upgrade on a T1. The proxy needs authentication though and synaptic didn't handle that well, so I couldn't connect via synaptic. Now, when I brough my computer back home and disabled theuse of the proxy from within Synaptic, apt starts spitting 404-errors at me whenever i try tp upgrade or update.
From home, I am using a direct connection to the internet and has never had any problems connecting before. Everything works, except apt, so i am writing this using the same connection as apt should be using.
This is a apt-get update: [http://pastebin.com/608901](http://pastebin.com/608901) (Too long to post here)
All the permissions on /var/lib/apt/lists seems to be as they should be:```
jeff@marisa:~$ ls -l /var/lib/apt/lists/
totalt 2604
-rw-r--r--  1 root root   13311 2006-03-15 16:41 archive.czessi.net_dists_breezy_Release
-rw-r--r--  1 root root    9233 2006-03-15 16:41 archive.czessi.net_dists_breezy_review_binary-i386_Packages
-rw-r--r--  1 root root   45898 2006-03-15 16:41 archive.czessi.net_dists_breezy_stable_binary-i386_Packages
-rw-r--r--  1 root root   41768 2006-03-15 16:41 archive.czessi.net_dists_breezy_stable-updates_binary-i386_Packages
-rw-r--r--  1 root root    3063 2006-03-15 16:41 archive.czessi.net_dists_breezy_testing_binary-i386_Packages
-rw-r--r--  1 root root    1421 2006-03-15 16:41 archive.czessi.net_dists_breezy_testing-updates_binary-i386_Packages
-rw-r--r--  1 root root    7864 2006-03-04 15:48 deb.svx.pl_dists_breezy_main_binary-i386_Packages
-rw-r--r--  1 root root    4419 2006-03-04 15:48 deb.svx.pl_dists_breezy_Release
-rw-r--r--  1 root root       0 2005-12-26 18:26 deb.svx.pl_dists_breezy_restricted_binary-i386_Packages
-rw-r--r--  1 root root   38913 2006-03-04 15:48 deb.svx.pl_dists_breezy_universe_binary-i386_Packages
-rw-r--r--  1 root root    1372 2005-12-18 03:31 ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages
-rw-r--r--  1 root root     445 2005-12-18 03:31 ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_source_Sources
-rw-r--r--  1 root root    5859 2005-12-18 03:31 ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages
-rw-r--r--  1 root root     872 2005-12-18 03:31 ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_source_Sources
-rw-r--r--  1 root root 1044400 2006-02-07 02:51 kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages
-rw-r--r--  1 root root    2327 2006-02-07 02:54 kubuntu.org_packages_kde351_dists_breezy_Release
-rw-r--r--  1 root root   56804 2006-03-14 16:19 kubuntu.org_packages_koffice-15beta2_dists_breezy_main_binary-i386_Packages
-rw-r--r--  1 root root    2336 2006-03-14 16:19 kubuntu.org_packages_koffice-15beta2_dists_breezy_Release
-rw-r-----  1 root root       0 2006-03-18 13:14 lock
-rw-r--r--  1 root root  124244 2006-03-03 00:19 mirror2.ubuntulinux.nl_dists_breezy-seveas_all_binary-i386_Packages
-rw-r--r--  1 root root   13070 2006-03-03 00:19 mirror2.ubuntulinux.nl_dists_breezy-seveas_backports_binary-i386_Packages
-rw-r--r--  1 root root   16113 2006-03-03 00:19 mirror2.ubuntulinux.nl_dists_breezy-seveas_custom_binary-i386_Packages
-rw-r--r--  1 root root   50133 2006-03-03 00:19 mirror2.ubuntulinux.nl_dists_breezy-seveas_drivers_binary-i386_Packages
-rw-r--r--  1 root root   19165 2006-03-03 00:19 mirror2.ubuntulinux.nl_dists_breezy-seveas_extras_binary-i386_Packages
-rw-r--r--  1 root root   10443 2006-03-03 00:19 mirror2.ubuntulinux.nl_dists_breezy-seveas_freenx_binary-i386_Packages
-rw-r--r--  1 root root    5688 2006-03-03 00:19 mirror2.ubuntulinux.nl_dists_breezy-seveas_java_binary-i386_Packages
-rw-r--r--  1 root root   10905 2006-03-03 00:19 mirror2.ubuntulinux.nl_dists_breezy-seveas_Release
-rw-r--r--  1 root root    9632 2006-03-03 00:19 mirror2.ubuntulinux.nl_dists_breezy-seveas_seveas-meta_binary-i386_Packages
-rw-r--r--  1 root root  124244 2006-03-03 00:19 mirror3.ubuntulinux.nl_dists_breezy-seveas_all_binary-i386_Packages
-rw-r--r--  1 root root   13070 2006-03-03 00:19 mirror3.ubuntulinux.nl_dists_breezy-seveas_backports_binary-i386_Packages
-rw-r--r--  1 root root   16113 2006-03-03 00:19 mirror3.ubuntulinux.nl_dists_breezy-seveas_custom_binary-i386_Packages
-rw-r--r--  1 root root   50133 2006-03-03 00:19 mirror3.ubuntulinux.nl_dists_breezy-seveas_drivers_binary-i386_Packages
-rw-r--r--  1 root root   19165 2006-03-03 00:19 mirror3.ubuntulinux.nl_dists_breezy-seveas_extras_binary-i386_Packages
-rw-r--r--  1 root root   10443 2006-03-03 00:19 mirror3.ubuntulinux.nl_dists_breezy-seveas_freenx_binary-i386_Packages
-rw-r--r--  1 root root    5688 2006-03-03 00:19 mirror3.ubuntulinux.nl_dists_breezy-seveas_java_binary-i386_Packages
-rw-r--r--  1 root root   10905 2006-03-03 00:19 mirror3.ubuntulinux.nl_dists_breezy-seveas_Release
-rw-r--r--  1 root root    9632 2006-03-03 00:19 mirror3.ubuntulinux.nl_dists_breezy-seveas_seveas-meta_binary-i386_Packages
drwxr-xr-x  2 root root    4096 2006-03-18 13:14 partial
-rw-r--r--  1 root root  115938 2006-01-07 13:24 people.ubuntu.com_%7edoko_OOo2_Packages
-rw-r--r--  1 root root       0 2006-01-07 13:24 people.ubuntu.com_%7edoko_OOo2_Sources
-rw-r--r--  1 root root  124244 2006-03-03 00:19 seveas.theplayboymansion.net_seveas_dists_breezy-seveas_all_binary-i386_Packages
-rw-r--r--  1 root root   13070 2006-03-03 00:19 seveas.theplayboymansion.net_seveas_dists_breezy-seveas_backports_binary-i386_Packages
-rw-r--r--  1 root root   16113 2006-03-03 00:19 seveas.theplayboymansion.net_seveas_dists_breezy-seveas_custom_binary-i386_Packages
-rw-r--r--  1 root root   50133 2006-03-03 00:19 seveas.theplayboymansion.net_seveas_dists_breezy-seveas_drivers_binary-i386_Packages
-rw-r--r--  1 root root   19165 2006-03-03 00:19 seveas.theplayboymansion.net_seveas_dists_breezy-seveas_extras_binary-i386_Packages
-rw-r--r--  1 root root   10443 2006-03-03 00:19 seveas.theplayboymansion.net_seveas_dists_breezy-seveas_freenx_binary-i386_Packages
-rw-r--r--  1 root root    5688 2006-03-03 00:19 seveas.theplayboymansion.net_seveas_dists_breezy-seveas_java_binary-i386_Packages
-rw-r--r--  1 root root   10905 2006-03-03 00:19 seveas.theplayboymansion.net_seveas_dists_breezy-seveas_Release
-rw-r--r--  1 root root    9632 2006-03-03 00:19 seveas.theplayboymansion.net_seveas_dists_breezy-seveas_seveas-meta_binary-i386_Packages
-rw-r--r--  1 root root   33495 2005-10-15 06:56 soulmachine.net_breezy_unstable_Packages
-rw-r--r--  1 root root     814 2005-10-17 21:09 soulmachine.net_breezy_unstable_Release
-rw-r--r--  1 root root  124244 2006-03-03 00:19 users.lichtsnel.nl_%7eseveas_dists_breezy-seveas_all_binary-i386_Packages
-rw-r--r--  1 root root   13070 2006-03-03 00:19 users.lichtsnel.nl_%7eseveas_dists_breezy-seveas_backports_binary-i386_Packages
-rw-r--r--  1 root root   16113 2006-03-03 00:19 users.lichtsnel.nl_%7eseveas_dists_breezy-seveas_custom_binary-i386_Packages
-rw-r--r--  1 root root   50133 2006-03-03 00:19 users.lichtsnel.nl_%7eseveas_dists_breezy-seveas_drivers_binary-i386_Packages
-rw-r--r--  1 root root   19165 2006-03-03 00:19 users.lichtsnel.nl_%7eseveas_dists_breezy-seveas_extras_binary-i386_Packages
-rw-r--r--  1 root root   10443 2006-03-03 00:19 users.lichtsnel.nl_%7eseveas_dists_breezy-seveas_freenx_binary-i386_Packages
-rw-r--r--  1 root root    5688 2006-03-03 00:19 users.lichtsnel.nl_%7eseveas_dists_breezy-seveas_java_binary-i386_Packages
-rw-r--r--  1 root root   10905 2006-03-03 00:19 users.lichtsnel.nl_%7eseveas_dists_breezy-seveas_Release
-rw-r--r--  1 root root    9632 2006-03-03 00:19 users.lichtsnel.nl_%7eseveas_dists_breezy-seveas_seveas-meta_binary-i386_Packages
-rw-r--r--  1 root root    3329 2006-03-12 23:08 wine.sourceforge.net_apt_binary_Packages
-rw-r--r--  1 root root     110 2005-07-28 23:08 wine.sourceforge.net_apt_binary_Release
-rw-r--r--  1 root root     112 2005-07-28 23:09 wine.sourceforge.net_apt_source_Release
-rw-r--r--  1 root root    2000 2006-03-12 23:08 wine.sourceforge.net_apt_source_Sources
-rw-r--r--  1 root root    6179 2006-02-21 12:31 www.informatik.uni-freiburg.de_%7emechnich_breezy_._Packages
jeff@marisa:~$      
```
Has anyone got any ideas about whats causing this? I am really bad at setting networking options in general in GNU/Linux and I don't know anything about networking with apt, so any tips or pointers would be appreciated.
Thanks!
Jeff

---

### Post by Treebeard on 2006-03-18
It's a guess, but if you look in /etc/apt/apt.conf, is there some line like this :

Proxy "http://....";

If there is, this is probably the proxy of your school. 
If you remove this line, it should work again..

---

### Post by Jeff Eklund on 2006-03-18
Guess I should've shown whats in my /etc/apt too...
```
jeff@marisa:~$ ls /etc/apt/
apt.conf.d   sources.list   trustdb.gpg  trusted.gpg~
secring.gpg  sources.list~  trusted.gpg
jeff@marisa:~$ ls /etc/apt/apt.conf.d/
05aptitude  10periodic  20archive  70debconf  99-localepurge  99update-notifier
jeff@marisa:~$

```
So that's not the problem. 
I don't really know what I may have done here, but it's freaking annoying not being able to apt-get anymore ;-)

---

### Post by Treebeard on 2006-03-18
Probably not, but is the "http_proxy" environment variable set? 
```

$ echo $http_proxy

or type "set"

``` 
Maybe try with cleaning the package information..
```

$ sudo apt-get clean

or

$sudo dpkg --clear-available

``` 
and then update again..

---

### Post by Jeff Eklund on 2006-03-18
echo $http_proxy gives:```

jeff@marisa:~$ echo $http_proxy
http://localhost:
```
Cleaning the apt cahce didn't help.

---

### Post by Jeff Eklund on 2006-03-22
Bump.
Life without apt sure is boring and lonely. Has no one got any suggestions on how to fix this?
Please, I am grateful for any little comment.

---

### Post by Ramses de Norre on 2006-03-22
> jeff@marisa:~$ ls /etc/apt/apt.conf.d/
05aptitude  10periodic  20archive  70debconf  99-localepurge  99update-notifier
That's a directory, you should check the file apt.conf instead.
```
less /etc/apt/apt.conf
```

---

### Post by Jeff Eklund on 2006-03-22
I know that's a directory. But I havent got any apt.conf file.
```
jeff@marisa:~$ ls /etc/apt/
apt.conf.d   sources.list   trustdb.gpg  trusted.gpg~
secring.gpg  sources.list~  trusted.gpg

jeff@marisa:~$ less /etc/apt/apt.conf
/etc/apt/apt.conf: No such file or directory

```

---

### Post by Treebeard on 2006-03-25
Does apt-get work when you log in e.g. tty1, not in Gnome/KDE 
(press ctrl + alt + F1) ?

---

### Post by Jeff Eklund on 2006-03-26
Sorry I didn't mention I fixed this. It was a env-variable that was somehow mysteriously set by a program I uninstalled a few weeks ago. But I got it working thanks to Soundray on the Ubuntu IRC-channel. Thanks!

---

