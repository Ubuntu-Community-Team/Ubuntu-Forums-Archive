---
title: "install print driver from .gz file"
date: 2012-02-07
forum: General Help
---

### Post by sks24 on 2012-02-07
I hate to ask about this, but I can't figure out how to install a print driver for a Samsung ML1865w printer from a .gz file.  I'm running 11.04 on an HP dm3 notebook.  
This was the driver I downloaded: [http://www.samsung.com/us/support/owners/product/ML-1865W/XAA#](http://www.samsung.com/us/support/owners/product/ML-1865W/XAA#)

I extracted the files to the desktop, and everything is in a folder which is called "cdroot"

Thanks in advance for your help with this.  
Scott

---

### Post by miasmablk on 2012-02-07
i assume you would just cd to the directory in which the files all extracted to then ./config --> make --> sudo make install the samsung website doesn't really give any instructions or list any depencies you'll need so you'll just have to go off of the error messages you get? some packeges i would suggest would be lib-cups lib-cups-dev build-essential

---

### Post by Gremlinzzz on 2012-02-07
:popcorn:
[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by sks24 on 2012-02-07
Thanks guys.

This is my dad's computer.  Next time I'm out there I'll give it another go!

---

### Post by miasmablk on 2012-02-07
yep, no prob :)

---

### Post by sks24 on 2012-02-18
Well, I'm stuck at: "chown: missing operand after" upon entering this command:  "sudo chown $roger /usr/local/src"

Full command sequence:  
```
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ tar -xzvf UnifiedLinuxDriver_0.98.tar.gz
tar (child): UnifiedLinuxDriver_0.98.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ sudo apt-get install build-essential checkinstall
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  checkinstall
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 135 kB of archives.
After this operation, 598 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/universe checkinstall amd64 1.6.2-1 [135 kB]
Fetched 135 kB in 3s (39.8 kB/s)       
Selecting previously deselected package checkinstall.
(Reading database ... 166034 files and directories currently installed.)
Unpacking checkinstall (from .../checkinstall_1.6.2-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up checkinstall (1.6.2-1) ...
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ sudo apt-get install cvs subversion git-core mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  emacsen-common git git-man libapr1 libaprutil1 liberror-perl libsvn1
  mercurial-common
Suggested packages:
  git-doc git-el git-arch git-cvs git-svn git-email git-daemon-run git-gui
  gitk gitweb qct wish vim emacs kdiff3 tkdiff meld xxdiff python-mysqldb
  python-pygments subversion-tools db4.8-util
The following NEW packages will be installed:
  cvs emacsen-common git git-core git-man libapr1 libaprutil1 liberror-perl
  libsvn1 mercurial mercurial-common subversion
0 upgraded, 12 newly installed, 0 to remove and 14 not upgraded.
Need to get 9,817 kB of archives.
After this operation, 26.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main cvs amd64 1:1.12.13-12ubuntu1 [1,716 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty/main emacsen-common all 1.4.19ubuntu2 [17.7 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ natty/main liberror-perl all 0.17-1 [23.8 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ natty/main git-man all 1:1.7.4.1-3 [579 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ natty/main git amd64 1:1.7.4.1-3 [4,658 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ natty/main git-core all 1:1.7.4.1-3 [1,380 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main libapr1 amd64 1.4.2-7ubuntu2.1 [87.8 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ natty/main libaprutil1 amd64 1.3.9+dfsg-5ubuntu3 [75.1 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main libsvn1 amd64 1.6.12dfsg-4ubuntu2.1 [815 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ natty/universe mercurial-common all 1.7.5-1ubuntu1 [1,484 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ natty/universe mercurial amd64 1.7.5-1ubuntu1 [61.8 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main subversion amd64 1.6.12dfsg-4ubuntu2.1 [298 kB]
Fetched 9,817 kB in 3min 55s (41.8 kB/s)                                       
Preconfiguring packages ...
Selecting previously deselected package cvs.
(Reading database ... 166065 files and directories currently installed.)
Unpacking cvs (from .../cvs_1%3a1.12.13-12ubuntu1_amd64.deb) ...
Selecting previously deselected package emacsen-common.
Unpacking emacsen-common (from .../emacsen-common_1.4.19ubuntu2_all.deb) ...
Selecting previously deselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package git-man.
Unpacking git-man (from .../git-man_1%3a1.7.4.1-3_all.deb) ...
Selecting previously deselected package git.
Unpacking git (from .../git_1%3a1.7.4.1-3_amd64.deb) ...
Selecting previously deselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.7.4.1-3_all.deb) ...
Selecting previously deselected package libapr1.
Unpacking libapr1 (from .../libapr1_1.4.2-7ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.3.9+dfsg-5ubuntu3_amd64.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.6.12dfsg-4ubuntu2.1_amd64.deb) ...
Selecting previously deselected package mercurial-common.
Unpacking mercurial-common (from .../mercurial-common_1.7.5-1ubuntu1_all.deb) ...
Selecting previously deselected package mercurial.
Unpacking mercurial (from .../mercurial_1.7.5-1ubuntu1_amd64.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.6.12dfsg-4ubuntu2.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up cvs (1:1.12.13-12ubuntu1) ...
Ignoring install-info called from maintainer script
The package cvs should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package cvs should be rebuilt with new debhelper to get trigger support
Setting up emacsen-common (1.4.19ubuntu2) ...
emacsen-common: Handling install of emacsen flavor emacs
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.7.4.1-3) ...
Setting up git (1:1.7.4.1-3) ...
Setting up git-core (1:1.7.4.1-3) ...
Setting up libapr1 (1.4.2-7ubuntu2.1) ...
Setting up libaprutil1 (1.3.9+dfsg-5ubuntu3) ...
Setting up libsvn1 (1.6.12dfsg-4ubuntu2.1) ...
Setting up mercurial-common (1.7.5-1ubuntu1) ...
Setting up mercurial (1.7.5-1ubuntu1) ...

Creating config file /etc/mercurial/hgrc.d/hgext.rc with new version
Setting up subversion (1.6.12dfsg-4ubuntu2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ sudo chown $roger /usr/local/src
chown: missing operand after `/usr/local/src'
Try `chown --help' for more information.
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ ^C
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ 

```

Again, thanks...

---

### Post by Leppie on 2012-02-18
the command should be either:
```
sudo chown $USER /usr/local/src
```
or:
```
sudo chown roger /usr/local/src
```

***However***, normally you don't want to change the owner in the /usr folders.
Is there a specific reason why you would want to change the owner?

---

### Post by mikejonesey on 2012-02-18
> **sks24 said:**
> Well, I'm stuck at: "chown: missing operand after" upon entering this command:  "sudo chown $roger /usr/local/src"

Full command sequence:  
```
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ tar -xzvf UnifiedLinuxDriver_0.98.tar.gz
tar (child): UnifiedLinuxDriver_0.98.tar.gz: Cannot open: No such file or directory
tar (child): Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error is not recoverable: exiting now
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ sudo apt-get install build-essential checkinstall
[sudo] password for roger: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  checkinstall
0 upgraded, 1 newly installed, 0 to remove and 14 not upgraded.
Need to get 135 kB of archives.
After this operation, 598 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/universe checkinstall amd64 1.6.2-1 [135 kB]
Fetched 135 kB in 3s (39.8 kB/s)       
Selecting previously deselected package checkinstall.
(Reading database ... 166034 files and directories currently installed.)
Unpacking checkinstall (from .../checkinstall_1.6.2-1_amd64.deb) ...
Processing triggers for man-db ...
Setting up checkinstall (1.6.2-1) ...
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ sudo apt-get install cvs subversion git-core mercurial
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following package was automatically installed and is no longer required:
  libnspr4-0d
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  emacsen-common git git-man libapr1 libaprutil1 liberror-perl libsvn1
  mercurial-common
Suggested packages:
  git-doc git-el git-arch git-cvs git-svn git-email git-daemon-run git-gui
  gitk gitweb qct wish vim emacs kdiff3 tkdiff meld xxdiff python-mysqldb
  python-pygments subversion-tools db4.8-util
The following NEW packages will be installed:
  cvs emacsen-common git git-core git-man libapr1 libaprutil1 liberror-perl
  libsvn1 mercurial mercurial-common subversion
0 upgraded, 12 newly installed, 0 to remove and 14 not upgraded.
Need to get 9,817 kB of archives.
After this operation, 26.3 MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ natty/main cvs amd64 1:1.12.13-12ubuntu1 [1,716 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ natty/main emacsen-common all 1.4.19ubuntu2 [17.7 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ natty/main liberror-perl all 0.17-1 [23.8 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ natty/main git-man all 1:1.7.4.1-3 [579 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ natty/main git amd64 1:1.7.4.1-3 [4,658 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ natty/main git-core all 1:1.7.4.1-3 [1,380 B]
Get:7 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main libapr1 amd64 1.4.2-7ubuntu2.1 [87.8 kB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ natty/main libaprutil1 amd64 1.3.9+dfsg-5ubuntu3 [75.1 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main libsvn1 amd64 1.6.12dfsg-4ubuntu2.1 [815 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ natty/universe mercurial-common all 1.7.5-1ubuntu1 [1,484 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ natty/universe mercurial amd64 1.7.5-1ubuntu1 [61.8 kB]
Get:12 http://us.archive.ubuntu.com/ubuntu/ natty-updates/main subversion amd64 1.6.12dfsg-4ubuntu2.1 [298 kB]
Fetched 9,817 kB in 3min 55s (41.8 kB/s)                                       
Preconfiguring packages ...
Selecting previously deselected package cvs.
(Reading database ... 166065 files and directories currently installed.)
Unpacking cvs (from .../cvs_1%3a1.12.13-12ubuntu1_amd64.deb) ...
Selecting previously deselected package emacsen-common.
Unpacking emacsen-common (from .../emacsen-common_1.4.19ubuntu2_all.deb) ...
Selecting previously deselected package liberror-perl.
Unpacking liberror-perl (from .../liberror-perl_0.17-1_all.deb) ...
Selecting previously deselected package git-man.
Unpacking git-man (from .../git-man_1%3a1.7.4.1-3_all.deb) ...
Selecting previously deselected package git.
Unpacking git (from .../git_1%3a1.7.4.1-3_amd64.deb) ...
Selecting previously deselected package git-core.
Unpacking git-core (from .../git-core_1%3a1.7.4.1-3_all.deb) ...
Selecting previously deselected package libapr1.
Unpacking libapr1 (from .../libapr1_1.4.2-7ubuntu2.1_amd64.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.3.9+dfsg-5ubuntu3_amd64.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.6.12dfsg-4ubuntu2.1_amd64.deb) ...
Selecting previously deselected package mercurial-common.
Unpacking mercurial-common (from .../mercurial-common_1.7.5-1ubuntu1_all.deb) ...
Selecting previously deselected package mercurial.
Unpacking mercurial (from .../mercurial_1.7.5-1ubuntu1_amd64.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.6.12dfsg-4ubuntu2.1_amd64.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
Processing triggers for doc-base ...
Processing 2 added doc-base file(s)...
Registering documents with scrollkeeper...
Setting up cvs (1:1.12.13-12ubuntu1) ...
Ignoring install-info called from maintainer script
The package cvs should be rebuilt with new debhelper to get trigger support
Ignoring install-info called from maintainer script
The package cvs should be rebuilt with new debhelper to get trigger support
Setting up emacsen-common (1.4.19ubuntu2) ...
emacsen-common: Handling install of emacsen flavor emacs
Setting up liberror-perl (0.17-1) ...
Setting up git-man (1:1.7.4.1-3) ...
Setting up git (1:1.7.4.1-3) ...
Setting up git-core (1:1.7.4.1-3) ...
Setting up libapr1 (1.4.2-7ubuntu2.1) ...
Setting up libaprutil1 (1.3.9+dfsg-5ubuntu3) ...
Setting up libsvn1 (1.6.12dfsg-4ubuntu2.1) ...
Setting up mercurial-common (1.7.5-1ubuntu1) ...
Setting up mercurial (1.7.5-1ubuntu1) ...

Creating config file /etc/mercurial/hgrc.d/hgext.rc with new version
Setting up subversion (1.6.12dfsg-4ubuntu2.1) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Processing triggers for python-support ...
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ sudo chown $roger /usr/local/src
chown: missing operand after `/usr/local/src'
Try `chown --help' for more information.
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ ^C
roger@roger-HP-Pavilion-dm3-Notebook-PC:~$ 

```Again, thanks...

I don't see $roger being set...

```
roger="$USER:$USER"; sudo chown $roger /usr/local/src
```or
```
roger="$USER"; sudo chown $roger /usr/local/src
```or
```
sudo chown $SUDO_USER /usr/local/src
``` or
```
sudo chown roger /usr/local/src
```

ps i'm not sure about chowning that dir... why? maybe chown the subdir created...

usually i make /usr/local dir's root:adm so only root or authorized users can mod installed software...

---

### Post by sks24 on 2012-02-18
"normally you don't want to change the owner in the /usr folders.
Is there a specific reason why you would want to change the owner?"
Well, I'm completely new to these .gz installations, and so ...no?  I was just trying to follow the instructions listed here: [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

Of course, if there were an easier way to do this, I would be delighted.
No hurry, though, as I have to leave now and it will be another week or two before I can return to this.  He can print while booted to Windows, so this isn't critical.  

Again, thanks for walking me through this.
SKS

---

### Post by Leppie on 2012-02-18
Most of the time, drivers can be compiled from the user's home folder.
I just downloaded the driver package.
If you go to the cdroot/ folder, you should issue the following command:
```
sudo ./autorun
```This will start the graphical installer. Make sure you install sane before running the autorun script:
```
sudo apt-get install sane
```

Once the installer has finished, you should be able to use the printer.

---

### Post by sks24 on 2012-02-18
Thank you, Leppie, for taking the time to do that.  I'm all about those graphical installers!  So thanks for getting me there, and I look forward to seeing this through next time I'm out there.

---

### Post by Leppie on 2012-02-18
Keep us posted.

---

