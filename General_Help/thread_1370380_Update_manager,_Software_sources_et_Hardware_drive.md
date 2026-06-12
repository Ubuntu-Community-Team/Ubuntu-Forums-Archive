---
title: "Update manager, Software sources et Hardware drivers applications don't open"
date: 2010-01-02
forum: General Help
---

### Post by danymboy on 2010-01-02
I just installed Ubuntu 9.10 and at some point I realised that the Update manager application will not open when I click on it the hard drive spin a little but nothing happens.

I realized that the Software sources et Hardware drivers apps are in the same states.  I was not able to see after what operation/installation I did that I they stop working.

I am a beginner with Linux, and I feel that if I reinstall I will fall into the same hole ... anyone has an idea for me to try?

---

### Post by sisco311 on 2010-01-02
Try to run them from a terminal (Applications -> Accessories -> Terminal)
and post the error message here.

```
update-manager
```
```
software-center
```

---

### Post by danymboy on 2010-01-02
dany@dany1:~$ update-manager
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 32, in <module>
    from UpdateManager.UpdateManager import UpdateManager
  File "/usr/lib/python2.6/dist-packages/UpdateManager/UpdateManager.py", line 36, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 25, in <module>
    from apt.package import Package
  File "/usr/lib/python2.6/dist-packages/apt/package.py", line 29, in <module>
    import urllib2
  File "/usr/lib/python2.6/urllib2.py", line 91, in <module>
    import hashlib
  File "/usr/lib/python2.6/hashlib.py", line 136, in <module>
    md5 = __get_builtin_constructor('md5')
  File "/usr/lib/python2.6/hashlib.py", line 63, in __get_builtin_constructor
    import _md5
ImportError: No module named _md5
dany@dany1:~$ 
dany@dany1:~$ 
dany@dany1:~$ 
dany@dany1:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 78, in <module>
    from softwarecenter.app import SoftwareCenterApp
  File "/usr/share/software-center/softwarecenter/app.py", line 41, in <module>
    from view.viewswitcher import ViewSwitcher, ViewSwitcherList
  File "/usr/share/software-center/softwarecenter/view/viewswitcher.py", line 19, in <module>
    import apt
  File "/usr/lib/python2.6/dist-packages/apt/__init__.py", line 25, in <module>
    from apt.package import Package
  File "/usr/lib/python2.6/dist-packages/apt/package.py", line 29, in <module>
    import urllib2
  File "/usr/lib/python2.6/urllib2.py", line 91, in <module>
    import hashlib
  File "/usr/lib/python2.6/hashlib.py", line 136, in <module>
    md5 = __get_builtin_constructor('md5')
  File "/usr/lib/python2.6/hashlib.py", line 63, in __get_builtin_constructor
    import _md5
ImportError: No module named _md5
dany@dany1:~$

---

### Post by sisco311 on 2010-01-02
Update your OS:
```
sudo apt-get update && sudo apt-get upgrade
```

After the update you may have to log out and log back in or reboot.

---

### Post by danymboy on 2010-01-02
I get the same errors on update-manager

Here is the output of:  sudo apt-get update && sudo apt-get upgrade

dany@dany1:~$ sudo apt-get update && sudo apt-get upgrade
[sudo] password for dany: 
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release.gpg
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release.gpg
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Translation-en_CA
Ign [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Translation-en_CA
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release.gpg
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Translation-en_CA
Ign [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Translation-en_CA
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates Release             
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Packages        
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) karmic-security/multiverse Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/universe Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) karmic-updates/multiverse Sources
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

P.S. thanks for your help its really appreciated

---

### Post by danymboy on 2010-01-02
I get the same error with this ... it seem that my Python install is somehow broken?

dany@dany1:/usr/lib/python2.6$ env python
Python 2.6.4 (r264:75706, Dec  7 2009, 18:43:55) 
[GCC 4.4.1] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> from hashlib import md5
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
  File "hashlib.py", line 136, in <module>
    md5 = __get_builtin_constructor('md5')
  File "hashlib.py", line 63, in __get_builtin_constructor
    import _md5
ImportError: No module named _md5
>>>

---

### Post by danymboy on 2010-01-02
I reinstalled the OS, it was one of my software (Druide Antidote HD)that break Python on install.

---

### Post by lpchouinard on 2010-01-12
Same here, after installing Antidote HD, it screw up python...

---

### Post by superRaccoon on 2010-09-11
same problem
I fixed it by updating Antidote HD from [http://www.druide.com/maj_linux.html](http://www.druide.com/maj_linux.html)
or 

wget [http://www.druide.com/telecharger/Linux/antidote_hd/Maj_Antidote_HD_v2_v4_Linux.tar.gz](http://www.druide.com/telecharger/Linux/antidote_hd/Maj_Antidote_HD_v2_v4_Linux.tar.gz)
tar -zxf Maj_Antidote_HD_v2_v4_Linux.tar.gz
sudo bash Maj_Antidote_HD_v2_v4_Linux.bash

obviously v2_v4 depend on which version you're from to new version

---

