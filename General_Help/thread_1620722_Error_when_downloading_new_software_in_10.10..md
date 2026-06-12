---
title: "Error when downloading new software in 10.10."
date: 2010-11-13
forum: General Help
---

### Post by laurenbanjo on 2010-11-13
Every time I download from the Ubuntu Software Center, it gets about 99% done and then it has an error.

The weird thing is that the applications are there and they work.

So, this isn't really a problem that I need fixed, I'm just wondering why this is. If someone knows how to fix it, that'd be cool because it is a bit annoying, especially last night when I downloaded about 10 things.

---

### Post by irv on 2010-11-13
> **laurenbanjo said:**
> Every time I download from the Ubuntu Software Center, it gets about 99% done and then it has an error.

The weird thing is that the applications are there and they work.

So, this isn't really a problem that I need fixed, I'm just wondering why this is. If someone knows how to fix it, that'd be cool because it is a bit annoying, especially last night when I downloaded about 10 things.
What does the error say? Have you tried installing software from the Synaptic Package Manager to see if you get the same error? Or maybe doing a install from the command prompt?

---

### Post by laurenbanjo on 2010-11-13
Attached is a screenshot of the error. It happens at the last second when it says "applying changes". I think that's why the applications still work, because I get no error when actually downloading them.

If you look, it even says "Finished"!

Here are the details of the error:

> installArchives() failed: Selecting previously deselected package visualboyadvance. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 162684 files and directories currently installed.) 
Unpacking visualboyadvance (from .../visualboyadvance_1.8.0-6_i386.deb) ... 
Selecting previously deselected package visualboyadvance-gtk. 
Unpacking visualboyadvance-gtk (from .../visualboyadvance-gtk_1.8.0-6_i386.deb) ... 
Processing triggers for man-db ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for python-gmenu ... 
Rebuilding /usr/share/applications/desktop.en_US.UTF8.cache... 
Processing triggers for menu ... 
Processing triggers for python-support ... 
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ... 
Not supported card here (PCI id 14e4:4727)! 
Use proper b43 or b43legacy firmware. 
Aborting. 
dpkg: error processing firmware-b43-lpphy-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 
No apport report written because MaxReports is reached already
Setting up visualboyadvance (1.8.0-6) ... 
Setting up visualboyadvance-gtk (1.8.0-6) ... 
Processing triggers for menu ... 
Errors were encountered while processing: 
 firmware-b43-lpphy-installer 
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ... 
Not supported card here (PCI id 14e4:4727)! 
Use proper b43 or b43legacy firmware. 
Aborting. 
dpkg: error processing firmware-b43-lpphy-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 


---

### Post by irv on 2010-11-13
Why don't you try installing something from the command line, but first do a 
```
sudo apt-get update
```
and then
```
sudo apt-get install "package name"
```

and see if you get the same errors.

---

### Post by coffeecat on 2010-11-13
If you look carefully at your errors, it is just one package that is the problem. That is why everything else installs OK.

> **laurenbanjo said:**
> Here are the details of the error:

```
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ... 
Not supported card here (PCI id 14e4:4727)! 
Use proper b43 or b43legacy firmware. 
Aborting. 
dpkg: error processing firmware-b43-lpphy-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1 

....

Errors were encountered while processing: 
 firmware-b43-lpphy-installer 
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ... 
Not supported card here (PCI id 14e4:4727)! 
Use proper b43 or b43legacy firmware. 
Aborting. 
dpkg: error processing firmware-b43-lpphy-installer (--configure): 
 subprocess installed post-installation script returned error exit status 1                       

```

The package firmware-b43-lpphy-installer is telling you it doesn't support your particular Broadcom card - ID 14e4:4727 - which a quick google shows is a BCM4313. The package information for that package says that it only supports the BCM4312. No doubt you have the correct Broadcom firmware installed, so I guess it would be safe to uninstall the firmware-b43-lpphy-installer package.

---

### Post by laurenbanjo on 2010-11-13
> **irv said:**
> Why don't you try installing something from the command line, but first do a 
```
sudo apt-get update
```and then
```
sudo apt-get install "package name"
```and see if you get the same errors.

This is what I got:

> laurenbanjo@Shane:~$ sudo apt-get update
[sudo] password for laurenbanjo: 
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release.gpg
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en
Ign [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/) maverick/main Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en  
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release  
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release.gpg
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/multiverse Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/universe Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [27.2kB]
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main Sources                         
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en
Ign [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick-updates/universe Translation-en_US
Hit [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick/main i386 Packages                     
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick Release                            
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main Sources                       
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick/multiverse i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [12.7kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/main i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/restricted i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/universe i386 Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) maverick-updates/multiverse i386 Packages
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe Sources [3,279B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse Sources [651B]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [36.3kB]
Get:8 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/universe i386 Packages [13.1kB]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/multiverse i386 Packages [1,660B]
Fetched 95.2kB in 6s (15.2kB/s)                                                
Reading package lists... Done
laurenbanjo@Shane:~$ sudo apt-get install bomberclone
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  bomberclone-data libmikmod2 libsdl-image1.2 libsdl-mixer1.2 libsmpeg0
The following NEW packages will be installed:
  bomberclone bomberclone-data libmikmod2 libsdl-image1.2 libsdl-mixer1.2
  libsmpeg0
0 upgraded, 6 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 8,229kB of archives.
After this operation, 10.1MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe libmikmod2 i386 3.1.11-a-6.3 [149kB]
Get:2 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe libsdl-image1.2 i386 1.2.10-2 [32.8kB]
Get:3 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe libsmpeg0 i386 0.4.5+cvs20030824-2.2 [102kB]
Get:4 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe libsdl-mixer1.2 i386 1.2.8-6build1 [99.1kB]
Get:5 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe bomberclone-data all 0.11.8-2 [7,756kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) maverick/universe bomberclone i386 0.11.8-2 [90.2kB]
Fetched 8,229kB in 25s (317kB/s)                                               
Selecting previously deselected package libmikmod2.
(Reading database ... 162711 files and directories currently installed.)
Unpacking libmikmod2 (from .../libmikmod2_3.1.11-a-6.3_i386.deb) ...
Selecting previously deselected package libsdl-image1.2.
Unpacking libsdl-image1.2 (from .../libsdl-image1.2_1.2.10-2_i386.deb) ...
Selecting previously deselected package libsmpeg0.
Unpacking libsmpeg0 (from .../libsmpeg0_0.4.5+cvs20030824-2.2_i386.deb) ...
Selecting previously deselected package libsdl-mixer1.2.
Unpacking libsdl-mixer1.2 (from .../libsdl-mixer1.2_1.2.8-6build1_i386.deb) ...
Selecting previously deselected package bomberclone-data.
Unpacking bomberclone-data (from .../bomberclone-data_0.11.8-2_all.deb) ...
Selecting previously deselected package bomberclone.
Unpacking bomberclone (from .../bomberclone_0.11.8-2_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up libmikmod2 (3.1.11-a-6.3) ...
Setting up libsdl-image1.2 (1.2.10-2) ...
Setting up libsmpeg0 (0.4.5+cvs20030824-2.2) ...
Setting up libsdl-mixer1.2 (1.2.8-6build1) ...
Setting up bomberclone-data (0.11.8-2) ...
Setting up bomberclone (0.11.8-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
 firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1)


---

### Post by irv on 2010-11-13
coffeecat is right on:
see your error
> Setting up firmware-b43-lpphy-installer (4.174.64.19-4) ...
Not supported card here (PCI id 14e4:4727)!
Use proper b43 or b43legacy firmware.
Aborting.
dpkg: error processing firmware-b43-lpphy-installer (--configure):
subprocess installed post-installation script returned error exit status 1
Setting up libmikmod2 (3.1.11-a-6.3) ...
Setting up libsdl-image1.2 (1.2.10-2) ...
Setting up libsmpeg0 (0.4.5+cvs20030824-2.2) ...
Setting up libsdl-mixer1.2 (1.2.8-6build1) ...
Setting up bomberclone-data (0.11.8-2) ...
Setting up bomberclone (0.11.8-2) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for menu ...
Errors were encountered while processing:
firmware-b43-lpphy-installer
E: Sub-process /usr/bin/dpkg returned an error code (1) 

---

