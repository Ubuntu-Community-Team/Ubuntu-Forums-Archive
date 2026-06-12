---
title: "Error: BrokenCount &gt; 0"
date: 2012-10-08
forum: General Help
---

### Post by Tovarishch on 2012-10-08
I keep running into 'Error: BrokenCount > 0', which started appearing after an update and a few program installs.

This is the error in more detail:
```
The following packages have unmet dependencies:

bind9-host: Depends: libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed
            Depends: libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed
            Depends: libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed
            Depends: libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed
            Depends: liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed
dnsutils: Depends: libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed
          Depends: libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed
          Depends: libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed
          Depends: libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed
          Depends: liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.2) but 1:9.8.1.dfsg.P1-4ubuntu0.3 is installed

```

I also tried to do a sudo apt-get install -f, but ran into this error:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libunity6 linux-headers-3.2.0-24 linux-headers-3.2.0-24-generic
  linux-headers-3.2.0-24-generic-pae
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  bind9-host dnsutils
Suggested packages:
  rblcheck
The following packages will be upgraded:
  bind9-host dnsutils
2 upgraded, 0 newly installed, 0 to remove and 361 not upgraded.
2 not fully installed or removed.
Need to get 0 B/197 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of bind9-host:
 bind9-host depends on libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of libbind9-80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
 bind9-host depends on libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of libdns81 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
 bind9-host depends on libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of libisc83 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
 bind9-host depends on libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of libisccfg82 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
 bind9-host depends on liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of liblwres80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
dpkg: error processing bind9-host (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          dpkg: dependency problems prevent configuration of dnsutils:
 dnsutils depends on libbind9-80 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of libbind9-80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
 dnsutils depends on libdns81 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of libdns81 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
 dnsutils depends on libisc83 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of libisc83 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
 dnsutils depends on libisccfg82 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of libisccfg82 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
 dnsutils depends on liblwres80 (= 1:9.8.1.dfsg.P1-4ubuntu0.2); however:
  Version of liblwres80 on system is 1:9.8.1.dfsg.P1-4ubuntu0.3.
 dnsutils depends on bind9-host | host; however:
  Package bind9-host is not configured yet.
  Package host is not installed.
  Package bind9-host which provides host is not configured yet.
dpkg: error processing dnsutils (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                          Errors were encountered while processing:
 bind9-host
 dnsutils
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

So what should I try to do to fix this? Thanks.

---

### Post by Tovarishch on 2012-10-09
**[Bump]** Still Unresolved.

---

### Post by dino99 on 2012-10-09
which ubuntu are you using ?
is it a genuine install ?
where come from the extra installed apps ?

Please post the result of that command into a terminal:

cat /etc/apt/sources.list

---

### Post by Tovarishch on 2012-10-09
> **dino99 said:**
> which ubuntu are you using ?
is it a genuine install ?
where come from the extra installed apps ?

Please post the result of that command into a terminal:

cat /etc/apt/sources.list

Using 12.04LTS 32Bit, and it is a genuine install dual-booted with windows 7.

```
cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted

# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise universe
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise multiverse
deb http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ natty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu precise-security main restricted
deb-src http://security.ubuntu.com/ubuntu precise-security main restricted
deb http://security.ubuntu.com/ubuntu precise-security universe
deb-src http://security.ubuntu.com/ubuntu precise-security universe
deb http://security.ubuntu.com/ubuntu precise-security multiverse
deb-src http://security.ubuntu.com/ubuntu precise-security multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
# deb http://archive.canonical.com/ubuntu natty partner
# deb-src http://archive.canonical.com/ubuntu natty partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main
```

Also apt-get update works fine but it doesn't do anything to fix the problem.

---

### Post by Tovarishch on 2012-10-09
**[Bump]** Still Unresolved.

---

### Post by Tovarishch on 2012-10-09
> **Tovarishch said:**
> **[Bump]** Still Unresolved.

I've tried everything I could think of, I don't know whatelse to do.

---

### Post by Tovarishch on 2012-10-09
I tried downloading the files separate from the Ubuntu packages, but it wouldn't let me install it.

Tried also to do apt-get clean and autoclean, and that didn't do anything either.

---

### Post by Tovarishch on 2012-10-10
[Bump] Unresolved still.

---

### Post by matt_symes on 2012-10-10
Hi

Let's have a look at the ppa's you have installed on your system as well as tha main sources.list file.

Open a terminal and type

```
grep -H -v ^# /etc/apt/sources.list.d/*
```This command is case sensitive so requires a capital H. Please post back the results.

This is an upgrade from Natty  ?

Kind regards

---

### Post by jrog on 2012-10-10
See if clearing APT's cache before attempting to fix broken packages helps:

```
sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```
Check if that fixes it. If it doesn't, you can try a bit more drastically clearing out old stuff and updating, using the following commands:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-bad
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo rm /var/cache/apt/*.bin
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by Tovarishch on 2012-10-10
> **matt_symes said:**
> Hi

Let's have a look at the ppa's you have installed on your system as well as tha main sources.list file.

Open a terminal and type

```
grep -H -v ^# /etc/apt/sources.list.d/*
```This command is case sensitive so requires a capital H. Please post back the results.

This is an upgrade from Natty  ?

Kind regards

It was a little awhile ago when I installed this, but I think it might of been an upgrade from Natty. I have two different systems with dual-boot, so I sometimes forget which was installed which.

Results:
```
Terminal:~$ grep -H -v ^# /etc/apt/sources.list.d/*
/etc/apt/sources.list.d/google-chrome.list:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/oneiric-partner.list:deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
/etc/apt/sources.list.d/oneiric-partner.list.distUpgrade:deb http://archive.canonical.com/ubuntu oneiric partner #Added by software-center
/etc/apt/sources.list.d/opera.list:
/etc/apt/sources.list.d/opera.list:deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera.list:
/etc/apt/sources.list.d/opera.list:
/etc/apt/sources.list.d/opera.list.distUpgrade:
/etc/apt/sources.list.d/opera.list.distUpgrade:deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera.list.distUpgrade:
/etc/apt/sources.list.d/opera.list.distUpgrade:

```

---

### Post by jrog on 2012-10-10
> **Tovarishch said:**
> It was a little awhile ago when I installed this, but I think it might of been an upgrade from Natty. I have two different systems with dual-boot, so I sometimes forget which was installed which.

Results:
```
Terminal:~$ grep -H -v ^# /etc/apt/sources.list.d/*
/etc/apt/sources.list.d/google-chrome.list:deb http://dl.google.com/linux/chrome/deb/ stable main
/etc/apt/sources.list.d/oneiric-partner.list:deb http://archive.canonical.com/ubuntu precise partner #Added by software-center
/etc/apt/sources.list.d/oneiric-partner.list.distUpgrade:deb http://archive.canonical.com/ubuntu oneiric partner #Added by software-center
/etc/apt/sources.list.d/opera.list:
/etc/apt/sources.list.d/opera.list:deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera.list:
/etc/apt/sources.list.d/opera.list:
/etc/apt/sources.list.d/opera.list.distUpgrade:
/etc/apt/sources.list.d/opera.list.distUpgrade:deb http://deb.opera.com/opera/ stable non-free #Opera Browser (final releases)
/etc/apt/sources.list.d/opera.list.distUpgrade:
/etc/apt/sources.list.d/opera.list.distUpgrade:

```
That output makes it look like you upgraded from Oneiric to Precise.

---

### Post by matt_symes on 2012-10-11
Hi

> /etc/apt/sources.list.d/oneiric-partner.list.distUpgrade:deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) oneiric partner #Added by software-center 

This ppa may be causing you a problem, i think, as it is for Oneric and you are using Precise.

Let's move it out the way for the moment. 

Open a terminal and type (or copy and paste)..

```
sudo mv /etc/apt/sources.list.d/oneiric-partner.list.distUpgrade ~
```

Enter your password. It will not be echoed to the screen. That will move that file to your home directory.

Then type 

```
sudo apt-get update
```

Then try

```
sudo apt-get install -f
```

Do you still get the same error ? You may well do but i suspect that ppa is causing you at least some problems.

Post back on the outcome and we can take it from there

Kind regards

---

### Post by jrog on 2012-10-11
> **matt_symes said:**
> This ppa may be causing you a problem, i think, as it is for Oneric and you are using Precise.
The filename for that PPA ends in '.distUpgrade'. That means APT will already ignore it. APT only processes files ending in '.list'. Notice that there is a duplicate version that ends in '.list' but that has been updated for the 'precise' PPA. This is part of the way that the Ubuntu upgrade process works -- it disables your PPAs by renaming them with .distUpgrade, so that they are backed up but not active. So, this shouldn't be a source of the OP's problems. (If it is, there's a bug somewhere in APT!)

---

### Post by matt_symes on 2012-10-12
Hi

> **jrog said:**
> The filename for that PPA ends in '.distUpgrade'. That means APT will already ignore it. APT only processes files ending in '.list'. Notice that there is a duplicate version that ends in '.list' but that has been updated for the 'precise' PPA. This is part of the way that the Ubuntu upgrade process works -- it disables your PPAs by renaming them with .distUpgrade, so that they are backed up but not active. So, this shouldn't be a source of the OP's problems. (If it is, there's a bug somewhere in APT!)

Good call. You are correct here.

Kind regards

---

### Post by Tovarishch on 2012-10-13
> **jrog said:**
> 
Check if that fixes it. If it doesn't, you can try a bit more drastically clearing out old stuff and updating, using the following commands:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-bad
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists/*
sudo mkdir /var/lib/apt/lists/partial
sudo rm /var/cache/apt/*.bin
sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
```

This has fixed the issue entirely, and now my distro works great. Thanks!

---

### Post by jrog on 2012-10-13
> **Tovarishch said:**
> This has fixed the issue entirely, and now my distro works great. Thanks!
Great! You're welcome!

By the way, if you encounter issues like this again, there is a good reference on the Wiki about troubleshooting package manager issues; it includes many of the commands that I gave you, though we skipped a few and left out some steps that weren't likely to be necessary in your case. You can find it here: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure)

---

