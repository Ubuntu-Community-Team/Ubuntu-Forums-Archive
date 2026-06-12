---
title: "Energy down during clamav installation"
date: 2009-12-29
forum: General Help
---

### Post by mag00 on 2009-12-29
Hello.

I have installed the clamav in my Karmic Koala and exactly after it finish the installation, I opened the clamtk for a first scan and the energy goes down.

Before the energy goes down the installation was finished OK and the clamtk was working normally.

After it, the clamtk doesnt open again. I tried to run the clamav directly from command line, and it doesnt work too. So I think that the energy break crashed some configuration files of clamav and tried to remove it completely for an re-installation.

Unfortunately it does not work. The system dont let me uninstall the clamav-freshclam package.

Can anyone help me with this trouble?

Above is some logs of my tries.

```
mag00@Q6600:~$ sudo dpkg --remove --force-remove-reinstreq clamav-freshclam
(Reading database ... 139696 files and directories currently installed.)
Removing clamav-freshclam ...
dpkg (subprocess): unable to execute installed pre-removal script: Exec format error
dpkg: error processing clamav-freshclam (--remove):
 subprocess installed pre-removal script returned error exit status 2
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 clamav-freshclam

```

```
mag00@Q6600:~$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libbit-vector-perl libcarp-clan-perl libconfig-tiny-perl libdate-calc-perl libdigest-hmac-perl libdigest-sha1-perl
  libfile-find-rule-perl libnet-dns-perl libnet-ip-perl libnumber-compare-perl libtext-glob-perl linux-headers-2.6.31-14
  linux-headers-2.6.31-14-generic
0 upgraded, 0 newly installed, 13 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 85.1MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 140710 files and directories currently installed.)
Removing libdate-calc-perl ...
Removing libbit-vector-perl ...
Removing libcarp-clan-perl ...
Removing libconfig-tiny-perl ...
Removing libnet-dns-perl ...
Removing libdigest-hmac-perl ...
Removing libdigest-sha1-perl ...
Removing libfile-find-rule-perl ...
Removing libnet-ip-perl ...
Removing libnumber-compare-perl ...
Removing libtext-glob-perl ...
Removing linux-headers-2.6.31-14-generic ...
Removing linux-headers-2.6.31-14 ...
Processing triggers for man-db ...
Setting up clamav-freshclam (0.95.3+dfsg-1ubuntu0.09.10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing clamav-freshclam (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 clamav-freshclam
 clamav-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
mag00@Q6600:~$ 
```

```
mag00@Q6600:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-daemon
mag00@Q6600:~$ 
```

```
mag00@Q6600:~$ sudo apt-get remove clamav --purge
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package clamav is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up clamav-freshclam (0.95.3+dfsg-1ubuntu0.09.10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing clamav-freshclam (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 clamav-freshclam
 clamav-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
mag00@Q6600:~$ 
```

```
mag00@Q6600:~$ sudo apt-get update
Hit http://br.archive.ubuntu.com karmic Release.gpg                                        
Ign http://br.archive.ubuntu.com karmic/main Translation-en_US                             
Ign http://br.archive.ubuntu.com karmic/restricted Translation-en_US        
Ign http://br.archive.ubuntu.com karmic/universe Translation-en_US          
Ign http://br.archive.ubuntu.com karmic/multiverse Translation-en_US        
Hit http://br.archive.ubuntu.com karmic-updates Release.gpg                 
Ign http://br.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://br.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://br.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://br.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://br.archive.ubuntu.com karmic Release       
Hit http://br.archive.ubuntu.com karmic-updates Release                     
Hit http://br.archive.ubuntu.com karmic/main Packages                       
Hit http://br.archive.ubuntu.com karmic/restricted Packages
Hit http://br.archive.ubuntu.com karmic/main Sources
Hit http://br.archive.ubuntu.com karmic/restricted Sources
Hit http://br.archive.ubuntu.com karmic/universe Packages
Hit http://br.archive.ubuntu.com karmic/universe Sources
Hit http://br.archive.ubuntu.com karmic/multiverse Packages
Hit http://br.archive.ubuntu.com karmic/multiverse Sources
Hit http://br.archive.ubuntu.com karmic-updates/main Packages
Hit http://br.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://br.archive.ubuntu.com karmic-updates/main Sources
Hit http://br.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://br.archive.ubuntu.com karmic-updates/universe Packages
Hit http://br.archive.ubuntu.com karmic-updates/universe Sources
Hit http://br.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://br.archive.ubuntu.com karmic-updates/multiverse Sources
Hit http://security.ubuntu.com karmic-security Release.gpg
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release
Hit http://security.ubuntu.com karmic-security/main Packages
Hit http://security.ubuntu.com karmic-security/restricted Packages
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Reading package lists... Done
mag00@Q6600:~$
```

```
mag00@Q6600:~$ sudo apt-get -f install clamav-daemon
Reading package lists... Done
Building dependency tree       
Reading state information... Done
clamav-daemon is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up clamav-freshclam (0.95.3+dfsg-1ubuntu0.09.10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing clamav-freshclam (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 clamav-freshclam
 clamav-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
mag00@Q6600:~$
```

```
mag00@Q6600:/var/cache/apt/archives$ sudo apt-get --reinstall install clamav
[sudo] password for mag00: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  clamav-docs
The following NEW packages will be installed:
  clamav
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 281kB of archives.
After this operation, 528kB of additional disk space will be used.
Get:1 http://br.archive.ubuntu.com karmic-updates/main clamav 0.95.3+dfsg-1ubuntu0.09.10 [281kB]
Fetched 281kB in 1s (274kB/s)  
Selecting previously deselected package clamav.
(Reading database ... 122908 files and directories currently installed.)
Unpacking clamav (from .../clamav_0.95.3+dfsg-1ubuntu0.09.10_amd64.deb) ...
Processing triggers for man-db ...
Setting up clamav-freshclam (0.95.3+dfsg-1ubuntu0.09.10) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing clamav-freshclam (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of clamav-daemon:
 clamav-daemon depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                Errors were encountered while processing:
 clamav-freshclam
 clamav-daemon
 clamav
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

[]'s

---

### Post by mag00 on 2009-12-29
OK. Lets try another question.

Lets suppose that dont exists "apt-get" or "synaptic". How I install, or better, unninstall the clamav-freshclam?!

[]'s

---

