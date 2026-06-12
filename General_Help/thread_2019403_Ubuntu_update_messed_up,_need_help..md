---
title: "Ubuntu update messed up, need help."
date: 2012-07-07
forum: General Help
---

### Post by BadUser on 2012-07-07
So what if I, possibly, theoretically, by being an impossible noob at  computers, managed to mess up my version of windows, and be out of money  at the same time. Then did a wubi install of ubuntu 11.10. And THEN  updated to 12.04. Managed to mess that up, and now nothing works. I  can't even install new packages (even though I'm on linux right now).
What works:

-Booting, I can get into Linux, go on the interwebz, no problem.

What doesn't: 
-Some  packages, And I can't install any new ones, also many packages that  should be installed automatically seem to be absent. (Like gparted for  instance). My screen is also not being recognised, so I'm stuck on 1280x768 instead of the native fullscreen resolution of 1080p.

As I said, I'm on a wubi install, I don't know if  formatting would work/be a good idea. I also don't have a working cd  reader, so any new installation would have to be via USB. I'm all outta  money too. Would appreciate help.



The error message I get when I try to install gparted (or any other package):
```
cyrus@ubuntu:~$ sudo apt-get install gparted
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 gparted : Depends: libgtkmm-2.4-1c2a (>= 1:2.24.0) but it is not going to be installed
 wine : Depends: wine1.5 but it is not going to be installed
 wine1.5-amd64 : Depends: wine1.5:any (= 1.5.8-0ubuntu1~pulse18)
                 Recommends: gettext but it is not going to be installed
                 Recommends: libcapi20-3 but it is not going to be installed
                 Recommends: unixodbc
                 Recommends: wine-gecko1.5 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```When I try sudo apt-get -f install:

```
dpkg: warning: files list file for package `wine1.5-i386:i386' missing, assuming package has no files currently installed.
(Reading database ... 319653 files and directories currently installed.)
Preparing to replace wine1.5-i386:i386 1.5.8-0ubuntu1~pulse18 (using .../wine1.5-i386_1.5.8-0ubuntu1~pulse18_i386.deb) ...
Unpacking replacement wine1.5-i386:i386 ...
dpkg: error processing /var/cache/apt/archives/wine1.5-i386_1.5.8-0ubuntu1~pulse18_i386.deb (--unpack):
 trying to overwrite '/usr/bin/wine-preloader', which is also in package wine1.4 1.4-0ubuntu1~ppa2~oneiric3
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 /var/cache/apt/archives/wine1.5-i386_1.5.8-0ubuntu1~pulse18_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```Lastly, when I start the software center it says:
```
Items cannot be installed or removed until the package catalogue is repaired, do you want to repair? (Repair/cancel)

```After I press repair:
```
   Package operation failed
   The installation or removal of a software package failed.
   
Details: 

   installArchives() failed: (Reading database ...  
dpkg: warning: files list file for package `wine1.5-i386:i386' missing, assuming package has no files currently installed. 
 (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 319653 files and directories currently installed.) 
Preparing to replace wine1.5-i386:i386 1.5.8-0ubuntu1~pulse18 (using .../wine1.5-i386_1.5.8-0ubuntu1~pulse18_i386.deb) ... 
Unpacking replacement wine1.5-i386:i386 ... 
dpkg: error processing /var/cache/apt/archives/wine1.5-i386_1.5.8-0ubuntu1~pulse18_i386.deb (--unpack): 
 trying to overwrite '/usr/bin/wine-preloader', which is also in package wine1.4 1.4-0ubuntu1~ppa2~oneiric3 
Errors were encountered while processing: 
 /var/cache/apt/archives/wine1.5-i386_1.5.8-0ubuntu1~pulse18_i386.deb 
Error in function:  
SystemError: E:Sub-process /usr/bin/dpkg returned an error code (1) 
dpkg: dependency problems prevent configuration of wine: 
 wine depends on wine1.5; however: 
  Package wine1.5 is not installed. 
dpkg: error processing wine (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of wine1.5-amd64: 
 wine1.5-amd64 depends on wine1.5:any (= 1.5.8-0ubuntu1~pulse18). 
dpkg: error processing wine1.5-amd64 (--configure): 
 dependency problems - leaving unconfigured

```


I don't know what to do. I'm on a wubi install of Ubuntu 12.04 (Which means it's in the same partition as windows or something.) After looking it up, apparently, 11.10 supported wubi installs, but 12.04 does not, however, downgrading seems nearly impossible. Any help, tips or solutions/diagnoses? :redface:



EDIT: Thanks for cleaning up my post a bit, it was quite the mess ^_^. I didn't know you had code tags either.

---

### Post by raja.genupula on 2012-07-07
hi open your terminal and type this one by  one and try again

```
sudo -i
apt-get autoremove
apt-get autoclean
apt-get install -f
```

---

### Post by BadUser on 2012-07-07
Nope, doesn't work, after the autoremove I get:

```
root@ubuntu:~# apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run ‘apt-get -f install’ to correct these.
The following packages have unmet dependencies.
 wine : Depends: wine1.5 but it is not installed
 wine1.5-amd64 : Depends: wine1.5:any (= 1.5.8-0ubuntu1~pulse18)
                 Recommends: gettext but it is not installed
                 Recommends: libcapi20-3 but it is not installed
                 Recommends: unixodbc
                 Recommends: wine-gecko1.5 but it is not installed
E: Unmet dependencies. Try using -f.

```

after autoclean:

```
root@ubuntu:~# apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Del wine1.5-i386 1.5.8-0ubuntu1~pulse18 [20.4 MB]

```

After install -f:

```
root@ubuntu:~# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libaccess-bridge-java libiso9660-7 libaccess-bridge-java-jni libvpx0
  libmatroska4 libjpeg62:i386 libllvm2.9:i386
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libcapi20-3:i386 unixodbc wine-gecko1.5:i386 wine1.5 wine1.5-i386:i386
Suggested packages:
  dosbox:any
Recommended packages:
  ttf-umefont gettext:i386 unixodbc:i386
The following packages will be REMOVED
  wine1.4
The following NEW packages will be installed
  libcapi20-3:i386 unixodbc wine-gecko1.5:i386 wine1.5
The following packages will be upgraded:
  wine1.5-i386:i386
1 upgraded, 4 newly installed, 1 to remove and 406 not upgraded.
3 not fully installed or removed.
Need to get 20.4 MB/37.5 MB of archives.
After this operation, 14.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/ precise/main wine1.5-i386 i386 1.5.8-0ubuntu1~pulse18 [20.4 MB]
Fetched 20.4 MB in 21s (947 kB/s)                                              
(Reading database ... 
dpkg: warning: files list file for package `wine1.5-i386:i386' missing, assuming package has no files currently installed.
(Reading database ... 319653 files and directories currently installed.)
Preparing to replace wine1.5-i386:i386 1.5.8-0ubuntu1~pulse18 (using .../wine1.5-i386_1.5.8-0ubuntu1~pulse18_i386.deb) ...
Unpacking replacement wine1.5-i386:i386 ...
dpkg: error processing /var/cache/apt/archives/wine1.5-i386_1.5.8-0ubuntu1~pulse18_i386.deb (--unpack):
 trying to overwrite '/usr/bin/wine-preloader', which is also in package wine1.4 1.4-0ubuntu1~ppa2~oneiric3
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 /var/cache/apt/archives/wine1.5-i386_1.5.8-0ubuntu1~pulse18_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Software center still tries to repair my package management, still fails. 
When I try to install gparted, I get the same error message as before.

---

### Post by steeldriver on 2012-07-07
do you have a ppa version of wine installed? just scanning your apt-get output seems to indicate that might be an issue

---

### Post by BadUser on 2012-07-07
I can't seem to add PPA's, when I try to do so in software center it asks me to repair my package manager or w/e and subsequently fails.
But to answer your question: I do have a ppa version of Wine windows programl loader installed (To play SC2)

---

### Post by steeldriver on 2012-07-07
it looks like you have an incomplete / misconfigured wine package - I guess you could try

```
sudo apt-get purge wine1.5-i386:i386 
```

---

### Post by BadUser on 2012-07-07
```
cyrus@ubuntu:~$ sudo apt-get purge wine1.5-i386:i386
[sudo] password for cyrus: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies.
 wine : Depends: wine1.5 but it is not going to be installed
 wine1.5-amd64 : Depends: wine1.5:any (= 1.5.8-0ubuntu1~pulse18)
                 Recommends: gettext but it is not going to be installed
                 Recommends: libcapi20-3 but it is not going to be installed
                 Recommends: unixodbc
                 Recommends: wine-gecko1.5 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Doesn't seem to work... :s

---

### Post by steeldriver on 2012-07-07
some further suggestions here, I can't vouch for any of them because it's never happened to me:

[http://askubuntu.com/questions/68257/cant-install-remove-upgrade-any-package](http://askubuntu.com/questions/68257/cant-install-remove-upgrade-any-package)

I would probably try the least obnoxious one first
```
sudo apt-get clean
```before trying stuff like manually editing /var/lib/dpkg/status

---

### Post by BadUser on 2012-07-07
Thanks, I guess I'll try that now :D

---

