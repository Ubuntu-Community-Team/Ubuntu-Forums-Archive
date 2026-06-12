---
title: "Frustrated....."
date: 2010-07-24
forum: General Help
---

### Post by aaronfox03 on 2010-07-24
Ive been searching for hours upon end today. I cannot get my Synaptic Package Manager to open AT ALL. Anything associated with it doesnt work either. I am pretty much stumped on what else to do or where else to look. Any help would be greatly appreciated!

---

### Post by howefield on 2010-07-24
> **aaronfox03 said:**
> I am pretty much stumped on what else to do or where else to look.

Try opening the application via a terminal, you may get a clue as to what the problem is in the output from the terminal.

```
gksudo synaptic
```

---

### Post by wojox on 2010-07-24
Open your terminal and run

```
sudo apt-get update; sudo apt-get upgrade
```

What errors does it show?

---

### Post by WorMzy on 2010-07-24
Also, try running ```
apt-get update
```
Synaptic is just a front end to apt, so if it's not working, there's likely a problem with apt, and 'apt-get update' should tell you what it is.

---

### Post by aaronfox03 on 2010-07-24
Errors were encountered while processing:
 kdepimlibs5
 libqt4-assistant
 libqt4-help
 libqt4-scripttools
 libqt4-test
 python-sip
 python-qt4
 python-kde4
 kdesudo
 gdebi-kde
 install-package
 libpackagekit-qt-12
 software-properties-kde
 libpackagekit-glib2-12
 python-packagekit
 packagekit-backend-apt
 packagekit
 update-manager-kde
 kpackagekit
 kubuntu-debug-installer
 libmysqlclient16
 libqt4-sql-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)



This is what I got after it went through everything.

---

### Post by WorMzy on 2010-07-24
After searching for that error, I found this [topic]("http://www.linuxquestions.org/questions/debian-26/sub-process-usr-bin-dpkg-returned-an-error-code-1-a-171107/"); which says that running ```
apt-get -f install
``` should clear it up. But I've also found suggestions that it may mean that your hard drive is full. So, check the disk usage analyser (baobab) if you have it installed to see if something's using up all your free space. If you don't have baobab installed, run
```
sudo du / | sort -nr | less
```
Be aware that this command will probably take a pretty long time to complete.

---

### Post by aaronfox03 on 2010-07-25
I can open it from the terminal, but I would still like to know what the problem is. I just did a clean install so there is nothing on my hard drive. I can download software, but I always get an error that says "Problem with removing software" or something like that. But even with that warning the software will still download. Using " sudo apt-get -f install" returns the same error as before. Thank you again for your help!

---

### Post by AlphaLexman on 2010-07-25
> **aaronfox03 said:**
> but I always get an error that says "Problem with removing software" or something like that.
Have you tried?:
```
sudo apt-get autoremove
```

---

### Post by aaronfox03 on 2010-07-25
Just tried and got the same error code...

---

### Post by AlphaLexman on 2010-07-25
OK, I would like to help, but lets almost start over...
What are you doing, typing in, to get the error message. I realise synaptic isn't running. 
Please post your commands that produce an error if from a terminal, or from the GUI.
Oh, and it helps if you use the 'quote' and 'code' tags from the toolbar.

---

### Post by aaronfox03 on 2010-07-25
If i try to download any thing from the software center, i get the "Problem loading Software" box. But when I look the software is downloaded. If I try to do updates through the GUI with Update manager, it will start to load then immediately close. I dont mind running everything through the Terminal, but there is obviously an issue somewhere. I cant really narrow it down because it happens when I download ANYTHING. Ive run all of the code advised in this post and all end with the same error.

---

### Post by AlphaLexman on 2010-07-25
I understand your frustration...
If you can be patient, and follow some commands in the terminal, (which gives more informed error messages) we can help you fix your problem.

Please post the output of:
```
sudo apt-get install fortune
```
Don't worry 'fortune' "should" be installed by default, it is just a simple 'fortune teller' of sorts. I am just trying to see what errors the system will output.

---

### Post by aaronfox03 on 2010-07-26
```
Note, selecting fortune-mod instead of fortune
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  fortune-mod fortunes-min librecode0
The following NEW packages will be installed:
  fortune-mod fortunes-min librecode0
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
22 not fully installed or removed.
Need to get 823kB of archives.
After this operation, 1,700kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ lucid/main librecode0 3.6-17 [702kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ lucid/main fortunes-min 1:1.99.1-3.1ubuntu4 [72.5kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ lucid/main fortune-mod 1:1.99.1-3.1ubuntu4 [48.4kB]
Fetched 823kB in 2s (285kB/s)       
Selecting previously deselected package librecode0.
(Reading database ... 161943 files and directories currently installed.)
Unpacking librecode0 (from .../librecode0_3.6-17_i386.deb) ...
Selecting previously deselected package fortunes-min.
Unpacking fortunes-min (from .../fortunes-min_1%3a1.99.1-3.1ubuntu4_all.deb) ...
Selecting previously deselected package fortune-mod.
Unpacking fortune-mod (from .../fortune-mod_1%3a1.99.1-3.1ubuntu4_i386.deb) ...
Processing triggers for man-db ...
Setting up kdepimlibs5 (4:4.4.2-0ubuntu2.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdepimlibs5 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-assistant (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-assistant (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-help (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-help (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-scripttools (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-scripttools (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up libqt4-test (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-test (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up python-sip (4.10.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-sip (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-qt4:
 python-qt4 depends on libqt4-assistant (>= 4:4.5.3); however:
  Package libqt4-assistant is not configured yet.
 python-qt4 depends on libqt4-help (>= 4:4.6.1); however:
  Package libqt4-help is not configured yet.
 python-qt4 depends on libqt4-scripttools (>= 4:4.6.1); however:
  Package libqt4-scripttools is not configured yet.
 python-qt4 depends on libqt4-test (>= 4:4.5.3); however:
  Package libqt4-test is not configured yet.
 python-qt4 depends on sip-api-7.0; however:
  Package sip-api-7.0 is not installed.
  Package python-sip which provides sip-api-7.0 is not configured yet.
dpkg: error processing python-qt4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-kde4:
 python-kde4 depends on kdepimlibs5 (>= 4:4.4.2); however:
  Package kdepimlibs5 is not configured yet.
 python-kde4 depends on python-qt4 (>= 4.7.2-0ubuntu1); however:
  Package python-qt4 is not configured yet.
 python-kde4 depends on sip-api-7.0; however:
  Package sip-api-7.0 is not installed.
  Package python-sip which provides sip-api-7.0 is not configured yet.
dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured
Setting up kdesudo (3.4.2.3-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdesudo (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of gdebi-kde:
 gdebi-kde depends on python-kde4 (>= 3.16.0-0ubuntu11); however:
  Package python-kde4 is not configured yet.
 gdebi-kde depends on kdesudo; however:
  Package kdesudo is not configured yet.
dpkg: error processing gdebi-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of install-package:
 install-package depends on gdebi-kde; however:
  Package gdebi-kde is not configured yet.
dpkg: error processing install-package (--configure):
 dependency problems - leaving unconfigured
Setting up libpackagekit-qt-12 (0.5.7-0ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpackagekit-qt-12 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of software-properties-kde:
 software-properties-kde depends on python-qt4; however:
  Package python-qt4 is not configured yet.
 software-properties-kde depends on python-kde4; however:
  Package python-kde4 is not configured yet.
 software-properties-kde depends on install-package; however:
  Package install-package is not configured yet.
dpkg: error processing software-properties-kde (--configure):
 dependency problems - leaving unconfigured
Setting up libpackagekit-glib2-12 (0.5.7-0ubuntu2) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpackagekit-glib2-12 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up python-packagekit (0.5.7-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-packagekit (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of packagekit-backend-apt:
 packagekit-backend-apt depends on python-packagekit (= 0.5.7-0ubuntu2); however:
  Package python-packagekit is not configured yet.
dpkg: error processing packagekit-backend-apt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of packagekit:
 packagekit depends on libpackagekit-glib2-12 (= 0.5.7-0ubuntu2); however:
  Package libpackagekit-glib2-12 is not configured yet.
 packagekit depends on packagekit-backend-apt | packagekit-backend-smart; however:
  Package packagekit-backend-apt is not configured yet.
  Package packagekit-backend-smart is not installed.
dpkg: error processing packagekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-kde:
 update-manager-kde depends on python-kde4; however:
  Package python-kde4 is not configured yet.
 update-manager-kde depends on kdesudo; howeverNo apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         :
  Package kdesudo is not configured yet.
dpkg: error processing update-manager-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kpackagekit:
 kpackagekit depends on libpackagekit-qt-12; however:
  Package libpackagekit-qt-12 is not configured yet.
 kpackagekit depends on software-properties-kde; however:
  Package software-properties-kde is not configured yet.
 kpackagekit depends on packagekit (>= 0.4.7); however:
  Package packagekit is not configured yet.
 kpackagekit depends on update-manager-kde; however:
  Package update-manager-kde is not configured yet.
dpkg: error processing kpackagekit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of kubuntu-debug-installer:
 kubuntu-debug-installer depends on kpackagekit; however:
  Package kpackagekit is not configured yet.
dpkg: error processing kubuntu-debug-installer (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Setting up libmysqlclient16 (5.1.41-3ubuntu12.3) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmysqlclient16 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt4-sql-mysql:
 libqt4-sql-mysql depends on libmysqlclient16 (>= 5.1.21-1); however:
  Package libmysqlclient16 is not configured yet.
dpkg: error processing libqt4-sql-mysql (--configure):
 dependency problems - leaving unconfigured
Setting up librecode0 (3.6-17) ...
No apport report written because MaxReports is reached already

Setting up fortunes-min (1:1.99.1-3.1ubuntu4) ...

Setting up fortune-mod (1:1.99.1-3.1ubuntu4) ...

Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 kdepimlibs5
 libqt4-assistant
 libqt4-help
 libqt4-scripttools
 libqt4-test
 python-sip
 python-qt4
 python-kde4
 kdesudo
 gdebi-kde
 install-package
 libpackagekit-qt-12
 software-properties-kde
 libpackagekit-glib2-12
 python-packagekit
 packagekit-backend-apt
 packagekit
 update-manager-kde
 kpackagekit
 kubuntu-debug-installer
 libmysqlclient16
 libqt4-sql-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Hopefully I did that right. Is this what youre asking for? Luckily im going to Afghanistan, so i have all the time in the world to mess with this.

---

### Post by AlphaLexman on 2010-07-26
> The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.

What kernel version are your using?
```
uname -r
```
Are your sources up to date:
```
sudo apt-get update
```
before you try to install anything?
Lets remove fortune (we'll reinstall later)
```
sudo apt-get remove fortune
```
Any errors? Post 'em.
If your kernel version is higher (greater than) 2.6.32-21 then try autoremove again.
```
sudo apt-get autoremove
```

---

### Post by aaronfox03 on 2010-07-26
```
 uname -r
2.6.32-24-generic

```

Was the output. I ran the other code and they all ran but ended with the same recurring error.

---

### Post by AlphaLexman on 2010-07-26
Please post the error results of:
```
sudo apt-get autoremove
```

---

### Post by aaronfox03 on 2010-07-26
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
22 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up kdepimlibs5 (4:4.4.2-0ubuntu2.1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdepimlibs5 (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-assistant (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-assistant (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-help (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-help (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up libqt4-scripttools (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-scripttools (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up libqt4-test (4:4.6.2-0ubuntu5) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libqt4-test (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up python-sip (4.10.1-0ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-sip (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-qt4:
 python-qt4 depends on libqt4-assistant (>= 4:4.5.3); however:
  Package libqt4-assistant is not configured yet.
 python-qt4 depends on libqt4-help (>= 4:4.6.1); however:
  Package libqt4-help is not configured yet.
 python-qt4 depends on libqt4-scripttools (>= 4:4.6.1); however:
  Package libqt4-scripttools is not configured yet.
 python-qt4 depends on libqt4-test (>= 4:4.5.3); however:
  Package libqt4-test is not configured yet.
 python-qt4 depends on sip-api-7.0; however:
  Package sip-api-7.0 is not installed.
  Package python-sip which provides sip-api-7.0 is not configured yet.
dpkg: error processing python-qt4 (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of python-kde4:
 python-kde4 depends on kdepimlibs5 (>= 4:4.4.2); however:
  Package kdepimlibs5 is not configured yet.
 python-kde4 depends on python-qt4 (>= 4.7.2-0ubuntu1); however:
  Package python-qt4 is not configured yet.
 python-kde4 depends on sip-api-7.0; however:
  Package sip-api-7.0 is not installed.
  Package python-sip which provides sip-api-7.0 is not configured yet.
dpkg: error processing python-kde4 (--configure):
 dependency problems - leaving unconfigured
Setting up kdesudo (3.4.2.3-0ubuntu1) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing kdesudo (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of gdebi-kde:
 gdebi-kde depends on python-kde4 (>= 3.16.0-0ubuntu11); however:
  Package python-kde4 is not configured yet.
 gdebi-kde depends on kdesudo; however:
  Package kdesudo is not configured yet.
dpkg: error processing gdebi-kde (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of install-package:
 install-package depends on gdebi-kde; however:
  Package gdebi-kde is not configured yet.
dpkg: error processing install-package (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            Setting up libpackagekit-qt-12 (0.5.7-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpackagekit-qt-12 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            dpkg: dependency problems prevent configuration of software-properties-kde:
 software-properties-kde depends on python-qt4; however:
  Package python-qt4 is not configured yet.
 software-properties-kde depends on python-kde4; however:
  Package python-kde4 is not configured yet.
 software-properties-kde depends on install-package; however:
  Package install-package is not configured yet.
dpkg: error processing software-properties-kde (--configure):
 dependency problems - leaving unconfigured
Setting up libpackagekit-glib2-12 (0.5.7-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libpackagekit-glib2-12 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              Setting up python-packagekit (0.5.7-0ubuntu2) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing python-packagekit (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of packagekit-backend-apt:
 packagekit-backend-apt depends on python-packagekit (= 0.5.7-0ubuntu2); however:
  Package python-packagekit is not configured yet.
dpkg: error processing packagekit-backend-apt (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of packagekit:
 packagekit depends on libpackagekit-glib2-12 (= 0.5.7-0ubuntu2); however:
  Package libpackagekit-glib2-12 is not configured yet.
 packagekit depends on packagekit-backend-apt | packagekit-backend-smart; however:
  Package packagekit-backend-apt is not configured yet.
  Package packagekit-backend-smart is not installed.
dpkg: error processing packagekit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of update-manager-kde:
 update-manager-kde depends on python-kde4; however:
  Package python-kde4 is not configured yet.
 update-manager-kde depends on kdesudo; however:
  Package kdesudo is not configured yet.
dpkg: error processing update-manager-kde (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kpackagekit:
 kpackagekit depends on libpackagekit-qt-12; however:
  Package libpackagekit-qt-12 is not configured yet.
 kpackagekit depends on software-properties-kde; however:
  Package software-properties-kde is not configured yet.
 kpackagekit depends on packagekit (>= 0.4.7); however:
  Package packagekit is not configured yet.
 kpackagekit depends on update-manager-kde; however:
  Package update-manager-kde is not configured yet.
dpkg: error processing kpackagekit (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of kubuntu-debug-installer:
 kubuntu-debug-installer depends on kpackagekit; however:
  Package kpackagekit is not configured yet.
dpkg: error processing kubuntu-debug-installer (--configure):
 dependency problems - leaving unconfigured
Setting up libmysqlclient16 (5.1.41-3ubuntu12.3) ...
No apport report written because MaxReports is reached already
                                                              dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing libmysqlclient16 (--configure):
 subprocess installed post-installation script returned error exit status 2
No apport report written because MaxReports is reached already
                                                              dpkg: dependency problems prevent configuration of libqt4-sql-mysql:
 libqt4-sql-mysql depends on libmysqlclient16 (>= 5.1.21-1); however:
  Package libmysqlclient16 is not configured yet.
dpkg: error processing libqt4-sql-mysql (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 kdepimlibs5
 libqt4-assistant
 libqt4-help
 libqt4-scripttools
 libqt4-test
 python-sip
 python-qt4
 python-kde4
 kdesudo
 gdebi-kde
 install-package
 libpackagekit-qt-12
 software-properties-kde
 libpackagekit-glib2-12
 python-packagekit
 packagekit-backend-apt
 packagekit
 update-manager-kde
 kpackagekit
 kubuntu-debug-installer
 libmysqlclient16
 libqt4-sql-mysql
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Dont know exactly where youre going with this or what youre looking for. So Ill just shoot you all of the output. I appreciate your help, guess this is a blessing in disguise cuz im becoming more proficient with the terminal. Thanks again!

---

### Post by AlphaLexman on 2010-07-26
I'm sorry, I really don't know where I am going either. I just keep asking for info, like throwing darts in the dark. I keep hoping, some clue will stand out, but thanks for your patience.

---

### Post by AlphaLexman on 2010-07-26
Are you using gnome with some qt4 apps or are you using kde (kubuntu)?

---

### Post by wojox on 2010-07-26
Are you running Kubuntu or Ubuntu? KDE or GNOME?

---

### Post by aaronfox03 on 2010-07-27
Ubuntu 10.04

---

### Post by AlphaLexman on 2010-07-27
Most of your errors are KDE related. Is there some kde / qt4 program you are attached to? A generic gnome / ubuntu install will not have all the libraries that are producing the errors.

---

### Post by linux18 on 2010-07-27
Probably, kde4 libs interfering caused by a broken package, some very careful commandlinefu is needed:

=================================================================
first, start in my own version of "safe mode"

STEP 1:
-choose recovery mode at grub

STEP 2:
-drop to a root prompt

STEP 3:
-type: 
```

telinit 3

``` and login

STEP 4:
-then type:
```

 xinit

```STEP 5:
-when xinit starts type:
```

metacity &

```- for ubuntu OR:
```

compiz &

```- if you have it OR flux/openbox & - if you have it OR:
```

fvwm4 & 

```- for xubuntu

STEP 6:
-then type:
```

 gnome panel & 

```-for ubuntu OR:
```

 xfce4-panel & 

```-for xubuntu

STEP 7:
-lastly type:
```
 
nm-applet & 

```-for networking
 
===============================================================
then fix synaptic:

```

 sudo apt-get -f || echo "ERROR 0"
 sudo rm /var/lib/apt/lists/partial/* || echo "ERROR 1: no partial packages - harmless error"
 sudo rm /var/cache/apt/*.bin || echo "ERROR 2"
 sudo apt-get clean || echo "ERROR 3"
 sudo apt-get autoclean || echo "ERROR 4"
 sudo apt-get autoremove || echo "ERROR 5"
 sudo apt-get update || echo "ERROR 6"
 sudo apt-get --fix-broken upgrade || echo "ERROR 7"
 sudo apt-get -f

```===============================================================

I'd also like to see the output starting with the " sudo apt-get -f || echo "error 0"

---

