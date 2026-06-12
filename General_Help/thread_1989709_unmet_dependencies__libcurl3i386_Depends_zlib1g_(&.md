---
title: "unmet dependencies:  libcurl3:i386: Depends: zlib1g (&gt;= 1:1.1.4) but 1:1.2.3.4.dfsg-3"
date: 2012-05-28
forum: General Help
---

### Post by naoyamakino on 2012-05-28
Hi there, I am having an issue whenever I try to install something. On Ubuntu Software Centre, I get a following error message when I try to install:


> The following packages have unmet dependencies:

libcurl3:i386: Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu4 is installed
libsasl2-modules:i386: Depends: libsasl2-2 (= 2.1.25.dfsg1-3ubuntu0.1) but 2.1.25.dfsg1-3ubuntu0.1 is installed
                       Depends: libc6 (>= 2.4) but 2.15-0ubuntu10 is installed

and here is what I get when I run sudo apt-get -f install


> @ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl1.0.0:i386
The following packages will be REMOVED:
  ttf-mscorefonts-installer
The following NEW packages will be installed:
  libssl1.0.0:i386
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,002 kB of archives.
After this operation, 2,743 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:amd64
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 170632 files and directories currently installed.)
Unpacking libssl1.0.0:i386 (from .../libssl1.0.0_1.0.1-4ubuntu5.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libssl1.0.0_1.0.1-4ubuntu5.2_i386.deb (--unpack):
 './usr/share/doc/libssl1.0.0/changelog.Debian.gz' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libssl1.0.0_1.0.1-4ubuntu5.2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


I am getting this error message when I try to repair installed software through Ubuntu Software Centre:

> installArchives() failed: Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
Preconfiguring packages ...
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:amd64
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.

(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 170632 files and directories currently installed.)
Unpacking libssl1.0.0:i386 (from .../libssl1.0.0_1.0.1-4ubuntu5.2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libssl1.0.0_1.0.1-4ubuntu5.2_i386.deb (--unpack):
 './usr/share/doc/libssl1.0.0/changelog.Debian.gz' is different from the same file on the system
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libssl1.0.0_1.0.1-4ubuntu5.2_i386.deb
Error in function: 
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1)



here is my version:

> naoyamakino@ubuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 12.04 LTS
Release:	12.04
Codename:	precise

I am new to ubuntu and not sure what I have done wrong. any feedback would be greatly appreciated.

regards

---

### Post by matt_symes on 2012-05-28
Hi

Open a terminal and type

```
sudo mv /usr/share/doc/libssl1.0.0/changelog.Debian.gz{,.old}
```

Then type 

```
sudo apt-get -f install
```

Can you also post the output of

```
grep -v ^# /etc/apt/sources.list /etc/apt/sources.list.d/*
```
Kind regards

---

### Post by naoyamakino on 2012-05-30
I think that worked, thanks!

> naoyamakino@ubuntu:~$ sudo mv /usr/share/doc/libssl1.0.0/changelog.Debian.gz{,.old}
[sudo] password for naoyamakino: 
naoyamakino@ubuntu:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libssl1.0.0:i386
The following packages will be REMOVED:
  ttf-mscorefonts-installer
The following NEW packages will be installed:
  libssl1.0.0:i386
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/1,002 kB of archives.
After this operation, 2,743 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Preconfiguring packages ...
dpkg: warning: there's no installed package matching ttf-mscorefonts-installer:amd64
(Reading database ... 
dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently installed.
(Reading database ... 170632 files and directories currently installed.)
Unpacking libssl1.0.0:i386 (from .../libssl1.0.0_1.0.1-4ubuntu5.2_i386.deb) ...
Setting up libssl1.0.0:i386 (1.0.1-4ubuntu5.2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
naoyamakino@ubuntu:~$ grep -v ^# /etc/apt/sources.list /etc/apt/sources.list.d/*/etc/apt/sources.list:
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise main restricted universe multiverse
/etc/apt/sources.list:deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) precise-security main restricted universe multiverse
/etc/apt/sources.list:deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) precise-updates main restricted universe multiverse
/etc/apt/sources.list.d/google-chrome.list.save:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/google.list.save:deb [http://dl.google.com/linux/chrome/deb/](http://dl.google.com/linux/chrome/deb/) stable main
/etc/apt/sources.list.d/pidgin-ppa.list:deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) precise main
/etc/apt/sources.list.d/pidgin-ppa.list:deb-src [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) precise main
/etc/apt/sources.list.d/pidgin-ppa.list.save:deb [http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu](http://ppa.launchpad.net/pidgin-developers/ppa/ubuntu) precise main
/etc/apt/sources.list.d/precise-partner.list:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
/etc/apt/sources.list.d/precise-partner.list.save:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner #Added by software-center
/etc/apt/sources.list.d/tualatrix-ppa-precise.list:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list:deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.save:deb [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/tualatrix-ppa-precise.list.save:deb-src [http://ppa.launchpad.net/tualatrix/ppa/ubuntu](http://ppa.launchpad.net/tualatrix/ppa/ubuntu) precise main
/etc/apt/sources.list.d/ubuntu-tweak-testing-ppa-precise.list:deb [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) precise main
/etc/apt/sources.list.d/ubuntu-tweak-testing-ppa-precise.list:deb-src [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) precise main

Do you see any issues with my /sources.list?

---

### Post by matt_symes on 2012-05-31
Hi

Your sources look fine to me so there is no problem there that i can see.

You do have a problem with ttf-mscorefonts-installer.

> dpkg: warning: files list file for package `ttf-mscorefonts-installer' missing, assuming package has no files currently 

I would try reinstalling that package.

From the terminal.

```
sudo apt-get clean
```

```
sudo apt-get install --reinstall ttf-mscorefonts-installer
```

Just to clean up what we did earlier type

```
sudo rm /usr/share/doc/libssl1.0.0/changelog.Debian.gz.old
```

Kind regards

---

### Post by naoyamakino on 2012-05-31
hi matt_symes, thank you so much for your help! much appreciated!

---

