---
title: "dpkg version warning on libreoffice-help-en-gb"
date: 2012-01-18
forum: General Help
---

### Post by Nick Payne on 2012-01-18
I'm running Ubuntu 10.04 amd64. The last couple of times I've run sudo apt-get update and then upgrade, I get a warning about a version number not starting with a digit, though this appears to be for a package that is not being updated. For example, this is the console output from the latest 'sudo apt-get upgrade':
```
nick@Nick-Ubuntu:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  garminplugin
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 161kB of archives.
After this operation, 4,096B of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://ppa.launchpad.net/andreas-diesner/garminplugin/ubuntu/ lucid/main garminplugin 0.3.7-1~lucid [161kB]
Fetched 161kB in 2s (65.6kB/s)       
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 25782 package 'libreoffice-help-en-gb':
 'Conflicts' field, reference to 'liblucene2-java': error in version: version number does not start with digit
(Reading database ... 261024 files and directories currently installed.)
Preparing to replace garminplugin 0.3.6-1~lucid (using .../garminplugin_0.3.7-1~lucid_amd64.deb) ...
Unpacking replacement garminplugin ...
Setting up garminplugin (0.3.7-1~lucid) ...
```
I don't appear to have libreoffice-help-en-gb installed, so what is causing this error:
```
nick@Nick-Ubuntu:~$ dpkg -s libreoffice-help-en-gb
Package `libreoffice-help-en-gb' is not installed and no info is available.
```

---

### Post by bbyrd on 2012-01-27
I was getting the same error. I actually did have libreoffice-help-en-gb installed. After purging it (sudo apt-get purge libreoffice-help-en-gb) I was able to upgrade libreoffice, but I cannot reinstall either libreoffice-help-en-gb or libreoffice-help-en-us - so I have no help files.

The error I get when trying to install libreoffice-help-en-gb is:

[SIZE="1"]dpkg: error processing /var/cache/apt/archives/libreoffice-help-en-gb_1%3a3.3.2-1ubuntu2~lucid1_all.deb (--unpack):
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 10 package 'libreoffice-help-en-gb':
 'Conflicts' field, reference to 'liblucene2-java': error in version: version number does not start with digit[/SIZE]

I had a look for the file/folder mentioned, but it doesn't exist - maybe a temp file created during the install attempt?

Anyone else have any ideas?

---

