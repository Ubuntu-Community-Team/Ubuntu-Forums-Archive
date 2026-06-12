---
title: "Error installing PHP5-Curl/Samba via apt-get"
date: 2010-12-02
forum: General Help
---

### Post by envisionsolutions on 2010-12-02
It seems that anything I try to install fails. I am not sure if it is that my sources.list is out of date. I tried updating the database but it doesn't seem to help. I am running Ubuntu 8.04. Can anyone help me?
 
Result of trying to install PHP5-curl:
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.166 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/main/source/Sources.gz) 404 Not Found [IP: 91.189.92.166 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.92.166 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.166 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/universe/source/Sources.gz) 404 Not Found [IP: 91.189.92.166 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/main/source/Sources.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.92.166 80]
W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/intrepid-security/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.92.166 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/restricted/source/Sources.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/universe/source/Sources.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.88.30 80]
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz](http://archive.ubuntu.com/ubuntu/dists/intrepid-updates/multiverse/source/Sources.gz) 404 Not Found [IP: 91.189.88.30 80]
E: Some index files failed to download, they have been ignored, or old ones used instead.
root@lamp1:~# apt-get install php5-curl
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
libcurl3
The following NEW packages will be installed:
libcurl3 php5-curl
0 upgraded, 2 newly installed, 0 to remove and 6 not upgraded.
Need to get 244kB of archives.
After this operation, 553kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
libcurl3 php5-curl
Install these packages without verification [y/N]? y
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main libcurl3 7.18.2-1ubuntu4.4
404 Not Found [IP: 91.189.92.166 80]
Err [http://security.ubuntu.com](http://security.ubuntu.com) intrepid-security/main php5-curl 5.2.6-2ubuntu4.6
404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.18.2-1ubuntu4.4_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/c/curl/libcurl3_7.18.2-1ubuntu4.4_i386.deb) 404 Not Found [IP: 91.189.92.166 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-curl_5.2.6-2ubuntu4.6_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-curl_5.2.6-2ubuntu4.6_i386.deb) 404 Not Found [IP: 91.189.92.166 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by sikander3786 on 2010-12-02
You are using Hardy but there are some entries in your sources.list that were intended for Jaunty. And support period for Jaunty is over.

Generate a new sources.list here.

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

Backup your existing sources.list by,

```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
```

Create a new one,

```
gksudo gedit /etc/apt/sources.list
```

Paste the newly genereted sources.list in here. Save and close and now,

```
sudo apt-get update
```

Hopefully, there will be no errors. If there are, please post the complete output.

Good Luck!

---

### Post by envisionsolutions on 2010-12-02
Thank you, that is a step in the right direction I think. Here is the error I now receive when I try to install curl. There were no errors when I ran apt-get update though. 
 

[EMAIL="root@lamp1"]root@lamp1[/EMAIL]:~# sudo apt-get install php5-curl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:
The following packages have unmet dependencies:
  php5-curl: Depends: php5-common (= 5.2.4-2ubuntu5.12) but 5.2.6-2ubuntu4.6 is to be installed
E: Broken packages

---

### Post by sikander3786 on 2010-12-03
First check your system for any other missing dependencies and try to fix them.

```
sudo apt-get install -f
```

```
sudo dpkg --configure -a
```

If no errors are reported, try installing php5-curl again and use aptitude this time.

```
sudo aptitude install php5-curl
```

---

### Post by envisionsolutions on 2010-12-03
Curl is installed but now I am unable to access any of my joomla websites. Error is Database Error: Unable to connect to the database:The MySQL adapter "mysql" is not available.
 
If there is any way you could provide some direction here, I was not expecting that to take me completely down, I've got several websites on this server.
 
It downgraded me to a version of php5 that was compatible with curl. Here was the process:
 
[EMAIL="root@lamp1"]root@lamp1[/EMAIL]:~# sudo apt-get install -f
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
[EMAIL="root@lamp1"]root@lamp1[/EMAIL]:~# sudo dpkg --configure -a
[EMAIL="root@lamp1"]root@lamp1[/EMAIL]:~# sudo aptitude install php5-curl
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
The following packages are BROKEN:
  php5-curl
0 packages upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
Need to get 23.7kB of archives. After unpacking 119kB will be used.
The following packages have unmet dependencies:
  php5-curl: Depends: php5-common (= 5.2.4-2ubuntu5.12) but 5.2.6-2ubuntu4.6 is                                                                                                                                                              installed.
The following actions will resolve these dependencies:
Remove the following packages:
php5-mysql
phpmyadmin
Downgrade the following packages:
libapache2-mod-php5 [5.2.6-2ubuntu4.6 (now) -> 5.2.4-2ubuntu5.12
(hardy-security, hardy-updates)]
php5-common [5.2.6-2ubuntu4.6 (now) -> 5.2.4-2ubuntu5.12 (hardy-security,
hardy-updates)]
php5-gd [5.2.6-2ubuntu4.6 (now) -> 5.2.4-2ubuntu5.12 (hardy-security,
hardy-updates)]
Score is 280
Accept this solution? [Y/n/q/?] y
The following packages will be DOWNGRADED:
  libapache2-mod-php5 php5-common php5-gd
The following NEW packages will be installed:
  php5-curl
The following packages will be REMOVED:
  libmcrypt4{u} php5-mcrypt{u} php5-mysql{a} phpmyadmin{a}
0 packages upgraded, 1 newly installed, 3 downgraded, 4 to remove and 5 not upgr                                                                                                                                                             aded.
Need to get 2849kB of archives. After unpacking 11.0MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main php5-gd 5.2.4-2ubuntu5.12                                                                                                                                                              [32.9kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main libapache2-mod-php5 5.2.4                                                                                                                                                             -2ubuntu5.12 [2475kB]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main php5-common 5.2.4-2ubuntu                                                                                                                                                             5.12 [317kB]
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-security/main php5-curl 5.2.4-2ubuntu5.                                                                                                                                                             12 [23.7kB]
Fetched 2849kB in 9s (310kB/s)
(Reading database ... 29626 files and directories currently installed.)
Removing phpmyadmin ...
 * Reloading web server config apache2                                   [ OK ]
Removing php5-mcrypt ...
Removing libmcrypt4 ...
Removing php5-mysql ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
dpkg - warning: downgrading php5-gd from 5.2.6-2ubuntu4.6 to 5.2.4-2ubuntu5.12.
(Reading database ... 28970 files and directories currently installed.)
Preparing to replace php5-gd 5.2.6-2ubuntu4.6 (using .../php5-gd_5.2.4-2ubuntu5.                                                                                                                                                             12_i386.deb) ...
Unpacking replacement php5-gd ...
dpkg - warning: downgrading libapache2-mod-php5 from 5.2.6-2ubuntu4.6 to 5.2.4-2                                                                                                                                                             ubuntu5.12.
Preparing to replace libapache2-mod-php5 5.2.6-2ubuntu4.6 (using .../libapache2-                                                                                                                                                             mod-php5_5.2.4-2ubuntu5.12_i386.deb) ...
Unpacking replacement libapache2-mod-php5 ...
dpkg - warning: downgrading php5-common from 5.2.6-2ubuntu4.6 to 5.2.4-2ubuntu5.                                                                                                                                                             12.
Preparing to replace php5-common 5.2.6-2ubuntu4.6 (using .../php5-common_5.2.4-2                                                                                                                                                             ubuntu5.12_i386.deb) ...
Unpacking replacement php5-common ...
Selecting previously deselected package php5-curl.
Unpacking php5-curl (from .../php5-curl_5.2.4-2ubuntu5.12_i386.deb) ...
Processing triggers for man-db ...
Setting up php5-common (5.2.4-2ubuntu5.12) ...
Installing new version of config file /etc/cron.d/php5 ...
Setting up libapache2-mod-php5 (5.2.4-2ubuntu5.12) ...
 * Reloading web server config apache2                                   [ OK ]
Setting up php5-gd (5.2.4-2ubuntu5.12) ...
Setting up php5-curl (5.2.4-2ubuntu5.12) ...
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done

It asked me which php.ini I wanted to use and I chose the local option which may have been wrong. It also removed phpmyadmin which I used. Is it possible to get it back? It uninstalled it for a reason I imagine.

---

### Post by envisionsolutions on 2010-12-03
I will pay for some help if there is someone willing. I really need to get this up.

---

### Post by sikander3786 on 2010-12-03
I feel sorry for your troubles. Hopefully, everything would soon be up and running again.

I think it would be better to start a new thread with your new problem under Server Platforms sub-forum.

Regarding phpmyadmin, did you try to re-install it via apt-get or aptitude?

---

