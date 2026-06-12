---
title: "error message"
date: 2009-10-26
forum: General Help
---

### Post by hotashes02 on 2009-10-26
every time i install something this massage pop-up 

```
E: ubuntu-tweak: subprocess post-installation script returned error exit status 2
```how i fix this?

---

### Post by Primefalcon on 2009-10-26
install through apt-get through a terminal, I think I know what's happening but just do this first....

---

### Post by mechro on 2009-10-26
Sorry, I couldn't resist....

I often pop-up during a massage.

:redface:

---

### Post by hotashes02 on 2009-10-26
> **Primefalcon said:**
> install through apt-get through a terminal, I think I know what's happening but just do this first....
how i do that?(sorry im new using linux)

---

### Post by Primefalcon on 2009-10-26
> **mechro said:**
> Sorry, I couldn't resist....

I often pop-up during a massage.

:redface:

LOL, my guess is he had a freeze or a shutdown or something in the middle of an installation or something previously and it's locked the dpkg up which means a file will need to be deleted form there

@hotashes02
what application are you trying to install?

---

### Post by Giblet5 on 2009-10-26
Remove ubuntu-tweak.

```
sudo apt-get remove ubuntu-tweak --purge
```

Contact the package maintainer (Google will tell you the goto guy) and tell him that his post-install script for Ubuntu is broken.

---

### Post by Primefalcon on 2009-10-26
> **Giblet5 said:**
> Remove ubuntu-tweak.

```
sudo apt-get remove ubuntu-tweak --purge
```

Contact the package maintainer (Google will tell you the goto guy) and tell him that his post-install script for Ubuntu is broken.
I doubt that would work...

---

### Post by hotashes02 on 2009-10-26
> **Giblet5 said:**
> Remove ubuntu-tweak.

```
sudo apt-get remove ubuntu-tweak --purge
```Contact the package maintainer (Google will tell you the goto guy) and tell him that his post-install script for Ubuntu is broken.

this what it give me

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-tweak*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 4903kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110015 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--purge):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by hotashes02 on 2009-10-26
the error still pop-up well i install something :'(

---

### Post by Primefalcon on 2009-10-26
> **hotashes02 said:**
> the error still pop-up well i install something :'(
I repeat what were you trying to install......

---

### Post by hotashes02 on 2009-10-26
> **Primefalcon said:**
> I repeat what were you trying to install......
vlc media player but it do the same with anything i try to install

---

### Post by Primefalcon on 2009-10-26
> **hotashes02 said:**
> vlc media player but it do the same with anything i try to install
As I said its more than likely a dpkg lock error but lets trace the file...

just run sudo apt-get install vlc

anbd post the error message here please

---

### Post by hotashes02 on 2009-10-26
> **Primefalcon said:**
> As I said its more than likely a dpkg lock error but lets trace the file...

just run sudo apt-get install vlc

anbd post the error message here please
: ) it install it but at end show the error

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libass3 libaudio2 libdvbpsi4 libebml0 libiso9660-5 liblua5.1-0 libmatroska0
  libqt4-dbus libqt4-designer libqt4-network libqt4-qt3support libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-xml libqtcore4 libqtgui4 libtar
  libvcdinfo0 libvlc2 libvlccore2 libxcb-keysyms0 qt4-qtconfig vlc-data
  vlc-nox
Suggested packages:
  nas libqt4-dev mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  libass3 libaudio2 libdvbpsi4 libebml0 libiso9660-5 liblua5.1-0 libmatroska0
  libqt4-dbus libqt4-designer libqt4-network libqt4-qt3support libqt4-script
  libqt4-sql libqt4-sql-mysql libqt4-xml libqtcore4 libqtgui4 libtar
  libvcdinfo0 libvlc2 libvlccore2 libxcb-keysyms0 qt4-qtconfig vlc vlc-data
  vlc-nox
0 upgraded, 26 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 21.5MB of archives.
After this operation, 66.8MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://ppa.launchpad.net jaunty/main libqtcore4 4.5.1-1~ppa1~jaunty1 [1505kB]
Get:2 http://us.archive.ubuntu.com jaunty/main libaudio2 1.9.1-5 [80.4kB]
Get:3 http://us.archive.ubuntu.com jaunty/universe libdvbpsi4 0.1.5-3.1 [32.6kB]
Get:4 http://us.archive.ubuntu.com jaunty/universe libebml0 0.7.7-3.1 [63.7kB]
Get:5 http://us.archive.ubuntu.com jaunty/universe libiso9660-5 0.78.2+dfsg1-3 [112kB]
Get:6 http://us.archive.ubuntu.com jaunty/main liblua5.1-0 5.1.4-2 [82.0kB]
Get:7 http://us.archive.ubuntu.com jaunty/universe libmatroska0 0.8.1-1.1 [196kB]
Get:8 http://us.archive.ubuntu.com jaunty/universe libtar 1.2.11-5ubuntu1 [20.4kB]
Get:9 http://us.archive.ubuntu.com jaunty/universe libvcdinfo0 0.7.23-4ubuntu1 [129kB]
Get:10 http://us.archive.ubuntu.com jaunty/main libxcb-keysyms0 0.2.1+git1-1 [7804B]
Get:11 http://ppa.launchpad.net jaunty/main libqt4-xml 4.5.1-1~ppa1~jaunty1 [84.8kB]
Get:12 http://ppa.launchpad.net jaunty/main libqt4-dbus 4.5.1-1~ppa1~jaunty1 [174kB]
Get:13 http://ppa.launchpad.net jaunty/main libqt4-script 4.5.1-1~ppa1~jaunty1 [345kB]
Get:14 http://ppa.launchpad.net jaunty/main libqtgui4 4.5.1-1~ppa1~jaunty1 [3616kB]
Get:15 http://ppa.launchpad.net jaunty/main libqt4-designer 4.5.1-1~ppa1~jaunty1 [1817kB]
Get:16 http://ppa.launchpad.net jaunty/main libqt4-network 4.5.1-1~ppa1~jaunty1 [386kB]
Get:17 http://ppa.launchpad.net jaunty/main libqt4-sql 4.5.1-1~ppa1~jaunty1 [85.5kB]
Get:18 http://ppa.launchpad.net jaunty/main libqt4-qt3support 4.5.1-1~ppa1~jaunty1 [1033kB]
Get:19 http://ppa.launchpad.net jaunty/main libqt4-sql-mysql 4.5.1-1~ppa1~jaunty1 [23.6kB]
Get:20 http://ppa.launchpad.net jaunty/main vlc-data 1.0.2-1~ppa1 [6712kB]     
Get:21 http://ppa.launchpad.net jaunty/main libvlccore2 1.0.2-1~ppa1 [408kB]   
Get:22 http://ppa.launchpad.net jaunty/main libvlc2 1.0.2-1~ppa1 [51.0kB]      
Get:23 http://ppa.launchpad.net jaunty/main qt4-qtconfig 4.5.1-1~ppa1~jaunty1 [80.7kB]
Get:24 http://ppa.launchpad.net jaunty/main libass3 0.9.6-1ubuntu1~ppa4 [51.8kB]
Get:25 http://ppa.launchpad.net jaunty/main vlc-nox 1.0.2-1~ppa1 [2743kB]      
Get:26 http://ppa.launchpad.net jaunty/main vlc 1.0.2-1~ppa1 [1630kB]          
Fetched 21.5MB in 40s (525kB/s)                                                
Selecting previously deselected package libaudio2.
(Reading database ... 109981 files and directories currently installed.)
Unpacking libaudio2 (from .../libaudio2_1.9.1-5_i386.deb) ...
Selecting previously deselected package libdvbpsi4.
Unpacking libdvbpsi4 (from .../libdvbpsi4_0.1.5-3.1_i386.deb) ...
Selecting previously deselected package libebml0.
Unpacking libebml0 (from .../libebml0_0.7.7-3.1_i386.deb) ...
Selecting previously deselected package libiso9660-5.
Unpacking libiso9660-5 (from .../libiso9660-5_0.78.2+dfsg1-3_i386.deb) ...
Selecting previously deselected package liblua5.1-0.
Unpacking liblua5.1-0 (from .../liblua5.1-0_5.1.4-2_i386.deb) ...
Selecting previously deselected package libmatroska0.
Unpacking libmatroska0 (from .../libmatroska0_0.8.1-1.1_i386.deb) ...
Selecting previously deselected package libqtcore4.
Unpacking libqtcore4 (from .../libqtcore4_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libqt4-xml.
Unpacking libqt4-xml (from .../libqt4-xml_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libqt4-dbus.
Unpacking libqt4-dbus (from .../libqt4-dbus_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libqt4-script.
Unpacking libqt4-script (from .../libqt4-script_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libqtgui4.
Unpacking libqtgui4 (from .../libqtgui4_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libqt4-designer.
Unpacking libqt4-designer (from .../libqt4-designer_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libqt4-network.
Unpacking libqt4-network (from .../libqt4-network_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libqt4-sql.
Unpacking libqt4-sql (from .../libqt4-sql_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libqt4-qt3support.
Unpacking libqt4-qt3support (from .../libqt4-qt3support_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libqt4-sql-mysql.
Unpacking libqt4-sql-mysql (from .../libqt4-sql-mysql_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libtar.
Unpacking libtar (from .../libtar_1.2.11-5ubuntu1_i386.deb) ...
Selecting previously deselected package libvcdinfo0.
Unpacking libvcdinfo0 (from .../libvcdinfo0_0.7.23-4ubuntu1_i386.deb) ...
Selecting previously deselected package vlc-data.
Unpacking vlc-data (from .../vlc-data_1.0.2-1~ppa1_all.deb) ...
Selecting previously deselected package libvlccore2.
Unpacking libvlccore2 (from .../libvlccore2_1.0.2-1~ppa1_i386.deb) ...
Selecting previously deselected package libvlc2.
Unpacking libvlc2 (from .../libvlc2_1.0.2-1~ppa1_i386.deb) ...
Selecting previously deselected package qt4-qtconfig.
Unpacking qt4-qtconfig (from .../qt4-qtconfig_4.5.1-1~ppa1~jaunty1_i386.deb) ...
Selecting previously deselected package libass3.
Unpacking libass3 (from .../libass3_0.9.6-1ubuntu1~ppa4_i386.deb) ...
Selecting previously deselected package libxcb-keysyms0.
Unpacking libxcb-keysyms0 (from .../libxcb-keysyms0_0.2.1+git1-1_i386.deb) ...
Selecting previously deselected package vlc-nox.
Unpacking vlc-nox (from .../vlc-nox_1.0.2-1~ppa1_i386.deb) ...
Selecting previously deselected package vlc.
Unpacking vlc (from .../vlc_1.0.2-1~ppa1_i386.deb) ...
Processing triggers for man-db ...
Setting up ubuntu-tweak (0.4.9.1-1~karmic3) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--configure):
 subprocess post-installation script returned error exit status 2
Setting up libaudio2 (1.9.1-5) ...

Setting up libdvbpsi4 (0.1.5-3.1) ...

Setting up libebml0 (0.7.7-3.1) ...

Setting up libiso9660-5 (0.78.2+dfsg1-3) ...

Setting up liblua5.1-0 (5.1.4-2) ...

Setting up libmatroska0 (0.8.1-1.1) ...

Setting up libqtcore4 (4.5.1-1~ppa1~jaunty1) ...

Setting up libqt4-xml (4.5.1-1~ppa1~jaunty1) ...

Setting up libqt4-dbus (4.5.1-1~ppa1~jaunty1) ...

Setting up libqt4-script (4.5.1-1~ppa1~jaunty1) ...

Setting up libqtgui4 (4.5.1-1~ppa1~jaunty1) ...

Setting up libqt4-designer (4.5.1-1~ppa1~jaunty1) ...

Setting up libqt4-network (4.5.1-1~ppa1~jaunty1) ...

Setting up libqt4-sql (4.5.1-1~ppa1~jaunty1) ...

Setting up libqt4-qt3support (4.5.1-1~ppa1~jaunty1) ...

Setting up libqt4-sql-mysql (4.5.1-1~ppa1~jaunty1) ...
Setting up libtar (1.2.11-5ubuntu1) ...

Setting up libvcdinfo0 (0.7.23-4ubuntu1) ...

Setting up vlc-data (1.0.2-1~ppa1) ...
Setting up libvlccore2 (1.0.2-1~ppa1) ...

Setting up libvlc2 (1.0.2-1~ppa1) ...

Setting up qt4-qtconfig (4.5.1-1~ppa1~jaunty1) ...

Setting up libass3 (0.9.6-1ubuntu1~ppa4) ...

Setting up libxcb-keysyms0 (0.2.1+git1-1) ...

Setting up vlc-nox (1.0.2-1~ppa1) ...
Setting up vlc (1.0.2-1~ppa1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

is possible to fix it? or i need to install ubuntu all over again :'(

---

### Post by Giblet5 on 2009-10-26
Try just running a cleanup:

```
sudo apt-get install -f
```

If that fails, drop down a level and use dpkg, then run a cleanup:

```
sudo dpkg -r ubuntu-tweak --force-remove-reinstreq
sudo apt-get install -f
```

---

### Post by Primefalcon on 2009-10-26
ok then did you crash when you were installing ubuntu tweak per chance or soemthing?

ok then try sudo apt-get remove -f ubuntu-tweak

there is actually nothing wrong with that program I run it myself

post results back here please

---

### Post by hotashes02 on 2009-10-26
> **Giblet5 said:**
> Try just running a cleanup:

```
sudo apt-get install -f
```If that fails, drop down a level and use dpkg, then run a cleanup:

```
sudo dpkg -r ubuntu-tweak --force-remove-reinstreq
sudo apt-get install -f
```
no it show the error at the end :(
```
yaiza@Ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ubuntu-tweak (0.4.9.1-1~karmic3) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
yaiza@Ubuntu:~$ sudo dpkg -r ubuntu-tweak --force-remove-reinstreq
(Reading database ... 110874 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
dpkg - warning: ignoring request to remove --force-remove-reinstreq which isn't installed.
Errors were encountered while processing:
 ubuntu-tweak
yaiza@Ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ubuntu-tweak (0.4.9.1-1~karmic3) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
yaiza@Ubuntu:~$ 

```

---

### Post by hotashes02 on 2009-10-26
> **Primefalcon said:**
> ok then did you crash when you were installing ubuntu tweak per chance or soemthing?

ok then try sudo apt-get remove -f ubuntu-tweak

there is actually nothing wrong with that program I run it myself

post results back here please
no it no crash in the process i install it today and update for ubuntu-tweak show up i did the update and that massage start to come up

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-tweak
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 4903kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110874 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by Primefalcon on 2009-10-26
> **hotashes02 said:**
> no i install it today and update for ubuntu-tweak show up i did the update and that massage start to come up

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-tweak
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 4903kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 110874 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

ok try this

sudo rm /var/lib/dpkg/info/ubuntu-tweak

---

### Post by Giblet5 on 2009-10-26
Can you try it one more time using this command?

I put the --force option in the wrong place.

```
sudo dpkg -r --force-remove-reinstreq ubuntu-tweak
sudo apt-get install -f
```

---

### Post by hotashes02 on 2009-10-26
> **Primefalcon said:**
> ok try this

sudo rm /var/lib/dpkg/info/ubuntu-tweak
it give this

```
yaiza@Ubuntu:~$ sudo rm /var/lib/dpkg/info/ubuntu-tweak
rm: cannot remove `/var/lib/dpkg/info/ubuntu-tweak': No such file or directory
yaiza@Ubuntu:~$ Primefalcon is online now Report Post   Reply With Quote

```

what is this??? 
```
Primefalcon is online now Report Post   Reply With Quote
```
:confused:

---

### Post by Giblet5 on 2009-10-26
> **Primefalcon said:**
> ok try this

sudo rm /var/lib/dpkg/info/ubuntu-tweak


I was saving that for when the 200 liters of gasoline and road flares didn't work. ;)

That will leave the scripts there...

---

### Post by hotashes02 on 2009-10-26
> **Giblet5 said:**
> Can you try it one more time using this command?

I put the --force option in the wrong place.

```
sudo dpkg -r --force-remove-reinstreq ubuntu-tweak
sudo apt-get install -f
```

Wow this going to be the 17 time that i have to start ubuntu all over again :cry:

```
yaiza@Ubuntu:~$ sudo dpkg -r --force-remove-reinstreq ubuntu-tweak
(Reading database ... 110874 files and directories currently installed.)
Removing ubuntu-tweak ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--remove):
 subprocess pre-removal script returned error exit status 2
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
yaiza@Ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ubuntu-tweak (0.4.9.1-1~karmic3) ...
Usage: update-python-modules [-v] [-c] package_directory [...]
       update-python-modules [-v] [-c] package.dirs [...]
       update-python-modules [-v] [-a|-f|-p]

update-python-modules: error: /usr/share/python-support/ubuntu-tweak.private is not a directory
dpkg: error processing ubuntu-tweak (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 ubuntu-tweak
E: Sub-process /usr/bin/dpkg returned an error code (1)
yaiza@Ubuntu:~$ 

```

---

### Post by Primefalcon on 2009-10-26
> **Giblet5 said:**
> I was saving that for when the 200 liters of gasoline and road flares didn't work. ;)

That will leave the scripts there...
;-) don't you just love the Ubuntu spirit though :-) when I was using windows it was hell trying to find one person to help..

my road flare response is to delete the lock files

---

### Post by hotashes02 on 2009-10-26
> **Primefalcon said:**
> ;-) don't you just love the Ubuntu spirit though :-) when I was using windows it was hell trying to find one person to help..

my road flare response is to delete the lock files

how i delete the lock files? i really don't want to start ubuntu all over again

---

### Post by Primefalcon on 2009-10-26
> **hotashes02 said:**
> how i delete the lock files?
try 

```
sudo rm /var/lib/dpkg/info/ubuntu-tweak 
```

first

---

### Post by Giblet5 on 2009-10-26
Let's remove the file that was supposed to be a directory, then create that directory and see if the postinstall can complete:

```
sudo rm -fr /usr/share/python-support/ubuntu-tweak.private
sudo mkdir /usr/share/python-support/ubuntu-tweak.private
sudo chmod 755 /usr/share/python-support/ubuntu-tweak.private
sudo apt-get install -f
```

---

### Post by hotashes02 on 2009-10-26
> **Primefalcon said:**
> try 

```
sudo rm /var/lib/dpkg/info/ubuntu-tweak 
```first

```
yaiza@Ubuntu:~$ sudo rm /var/lib/dpkg/info/ubuntu-tweak
rm: cannot remove `/var/lib/dpkg/info/ubuntu-tweak': No such file or directory
yaiza@Ubuntu:~$ 

```

---

### Post by Giblet5 on 2009-10-26
> **Primefalcon said:**
> try 

```
sudo rm /var/lib/dpkg/info/ubuntu-tweak 
```

first

He did that.

It was not found.

It shouldn't be found because there should be no such file there.

/var/lib/dpkg/info/ubuntu-tweak.conffiles
/var/lib/dpkg/info/ubuntu-tweak.list
/var/lib/dpkg/info/ubuntu-tweak.md5sum

THOSE will be there...

---

### Post by hotashes02 on 2009-10-26
> **Giblet5 said:**
> Let's remove the file that was supposed to be a directory, then create that directory and see if the postinstall can complete:

```
sudo rm -fr /usr/share/python-support/ubuntu-tweak.private
sudo mkdir /usr/share/python-support/ubuntu-tweak.private
sudo chmod 755 /usr/share/python-support/ubuntu-tweak.private
sudo apt-get install -f
```

yeahhhhh!!! the massage is gone!!!  :guitar:
[Primefalcon]("http://ubuntuforums.org/member.php?u=543184") and [Giblet5]("http://ubuntuforums.org/member.php?u=162554") thank a lot you 2 ROCK!

```
yaiza@Ubuntu:~$ sudo rm /var/lib/dpkg/info/ubuntu-tweak
rm: cannot remove `/var/lib/dpkg/info/ubuntu-tweak': No such file or directory
yaiza@Ubuntu:~$ sudo rm -fr /usr/share/python-support/ubuntu-tweak.private
yaiza@Ubuntu:~$ sudo mkdir /usr/share/python-support/ubuntu-tweak.private
yaiza@Ubuntu:~$ sudo chmod 755 /usr/share/python-support/ubuntu-tweak.private
yaiza@Ubuntu:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up ubuntu-tweak (0.4.9.1-1~karmic3) ...

Processing triggers for python-support ...
yaiza@Ubuntu:~$ 

```

---

### Post by Giblet5 on 2009-10-26
> **Giblet5 said:**
> Let's remove the file that was supposed to be a directory, then create that directory and see if the postinstall can complete:

```
sudo rm -fr /usr/share/python-support/ubuntu-tweak.private
sudo mkdir /usr/share/python-support/ubuntu-tweak.private
sudo chmod 755 /usr/share/python-support/ubuntu-tweak.private
sudo apt-get install -f
```


That will probably eliminate the error and the install might complete.

I'd still remove the package but it might work when you're done.

---

### Post by Giblet5 on 2009-10-26
> **hotashes02 said:**
> yeahhhhh!!! the massage is gone!!!  :guitar:

Meh. If we rocked, the guitar would have come in the third comment. :)

---

### Post by Primefalcon on 2009-10-26
why not just have a full concert :-)

---

### Post by arielon on 2009-11-07
Ok, supers, here's my little one, to see if u can lend me a hand...):P

```
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up bcmwl-kernel-source (5.10.91.9+bdcom-0ubuntu4) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing bcmwl-kernel-source (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up fakeroot (1.12.4ubuntu1) ...
dpkg (subprocess): unable to execute installed post-installation script: Exec format error
dpkg: error processing fakeroot (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 bcmwl-kernel-source
 fakeroot
E: Sub-process /usr/bin/dpkg returned an error code (1)
```currently doing the .private thing... (dunno if is right) with fakeroot.private ([find -name fakeroot.private], as i don't know where to look).

Thanks!

EDIT1: Nothing found with ```
sudo find / -name fakeroot.private
```

---

