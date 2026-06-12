---
title: "Cannot apt-get install"
date: 2009-07-03
forum: General Help
---

### Post by MimziM on 2009-07-03
For some reason I cannot open synaptic package manager
There are no errors, ialso I can open add/remove and view 
but cannot install or remove anything.
When I apt get I get this:
```
 damian@Badass:~$ sudo apt-get update
Hit http://gb.archive.ubuntu.com intrepid Release.gpg
Hit http://gb.archive.ubuntu.com intrepid/main Translation-en_GB
Hit http://security.ubuntu.com intrepid-security Release.gpg
Ign http://security.ubuntu.com intrepid-security/main Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates Release.gpg
Hit http://gb.archive.ubuntu.com intrepid-updates/main Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/restricted Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/universe Translation-en_GB
Ign http://security.ubuntu.com intrepid-security/multiverse Translation-en_GB
Hit http://gb.archive.ubuntu.com intrepid Release
Hit http://security.ubuntu.com intrepid-security Release
Hit http://gb.archive.ubuntu.com intrepid-updates Release
Hit http://gb.archive.ubuntu.com intrepid/main Packages             
Hit http://security.ubuntu.com intrepid-security/main Packages
Hit http://gb.archive.ubuntu.com intrepid/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid/main Sources
Hit http://gb.archive.ubuntu.com intrepid/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid/universe Packages
Hit http://security.ubuntu.com intrepid-security/restricted Packages
Hit http://security.ubuntu.com intrepid-security/main Sources
Hit http://security.ubuntu.com intrepid-security/restricted Sources
Hit http://security.ubuntu.com intrepid-security/universe Packages
Hit http://gb.archive.ubuntu.com intrepid/universe Sources
Hit http://gb.archive.ubuntu.com intrepid/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/main Packages
Hit http://security.ubuntu.com intrepid-security/universe Sources
Hit http://security.ubuntu.com intrepid-security/multiverse Packages
Hit http://security.ubuntu.com intrepid-security/multiverse Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/main Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/restricted Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/universe Sources
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Packages
Hit http://gb.archive.ubuntu.com intrepid-updates/multiverse Sources
Reading package lists... Done
damian@Badass:~$ sudo apt-get install update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package update
damian@Badass:~$ 
 
```

I've tried apt-get upgrade
but it doesnt change anything
Anyone have any ideas
even if not cure, just diagnose??

---

### Post by Idefix82 on 2009-07-03
The syntax for installing a package is
```
sudo apt-get install packagename
```
where packagename is the name if the package you want to install. What you typed makes apt-get look for a package named update and that doesn't exist.

---

### Post by MimziM on 2009-07-03
even when my update manager tells me there are updates
I open it and it shows the updates I need but  won't install them
it tries, it says "reading package information" then it just goes back to 
update manager without installing them and the text of each update on the
list is cut in half

---

### Post by DougieFresh4U on 2009-07-03
How about trying
```
sudo apt-get dist-upgrade
sudo apt-get -f install 
sudo dpkg --configure -a
```
in that order one at a time

---

### Post by MimziM on 2009-07-03
```
damian@Badass:~$ sudo apt-get dist-upgrade
[sudo] password for damian: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
damian@Badass:~$ sudo apt-get -f install 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.27-7 linux-headers-2.6.27-7-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
damian@Badass:~$ sudo dpkg --configure -a
damian@Badass:~$

```
still cannot open synaptic package manager, or apt-get any packages
What if if booted under previous headers updated from there would it over write similar headers or would it just tell me they already exist?

---

