---
title: "apt-get time out"
date: 2011-07-20
forum: General Help
---

### Post by clement_911 on 2011-07-20
Hi all.
 
I'm trying to install the samba client package by running the following command:
[INDENT]*sudo apt-get install smbfs*
[/INDENT]However, it hangs forever and times out on us.archive.ubuntu.com:
[INDENT]*Reading package lists... Done*
*Building dependency tree *
*Reading state information... Done*
*The following extra packages will be installed:*
*cifs-utils*
*The following NEW packages will be installed:*
*cifs-utils smbfs*
*0 upgraded, 2 newly installed, 0 to remove and 144 not upgraded.*
*Need to get 41.2 kB of archives.*
*After this operation, 184 kB of additional disk space will be used.*
*Do you want to continue [Y/n]? Y*
*0% [Connecting to us.archive.ubuntu.com (91.189.92.169)]*
 
[/INDENT]My internet connection is fine. I can ping us.archive.ubuntu.com and even browse the folders in Firefox.
 
My /etc/apt/sources.list is pointing to [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/)
I've tried pointing to uk.archive.ubuntu.com and archive.ubuntu.com but then the package is not found:
[INDENT]*Package smbfs is not available, but is referred to by another package.*
*This may mean that the package is missing, has been obsoleted, or*
*is only available from another source*
*E: Package 'smbfs' has no installation candidate*
 
[/INDENT]Here is my full sources.list:
[INDENT]*#deb cdrom:[Ubuntu 11.04 _Natty Narwhal_ - Release i386 (20110427.1)]/ natty main restricted*
*# See *[*http://help.ubuntu.com/community/UpgradeNotes*]("http://help.ubuntu.com/community/UpgradeNotes")* for how to upgrade to*
*# newer versions of the distribution.*
*deb *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty main restricted*
*deb-src *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty main restricted*
*## Major bug fix updates produced after the final release of the*
*## distribution.*
*deb *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty-updates main restricted*
*deb-src *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty-updates main restricted*
*## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu*
*## team. Also, please note that software in universe WILL NOT receive any*
*## review or updates from the Ubuntu security team.*
*deb *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty universe*
*deb-src *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty universe*
*deb *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty-updates universe*
*deb-src *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty-updates universe*
*## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu *
*## team, and may not be under a free licence. Please satisfy yourself as to *
*## your rights to use the software. Also, please note that software in *
*## multiverse WILL NOT receive any review or updates from the Ubuntu*
*## security team.*
*deb *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty multiverse*
*deb-src *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty multiverse*
*deb *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty-updates multiverse*
*deb-src *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty-updates multiverse*
*## Uncomment the following two lines to add software from the 'backports'*
*## repository.*
*## N.B. software from this repository may not have been tested as*
*## extensively as that contained in the main release, although it includes*
*## newer versions of some applications which may provide useful features.*
*## Also, please note that software in backports WILL NOT receive any review*
*## or updates from the Ubuntu security team.*
*# deb *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty-backports main restricted universe multiverse*
*# deb-src *[*http://us.archive.ubuntu.com/ubuntu/*]("http://us.archive.ubuntu.com/ubuntu/")* natty-backports main restricted universe multiverse*
*deb *[*http://security.ubuntu.com/ubuntu*]("http://security.ubuntu.com/ubuntu")* natty-security main restricted*
*deb-src *[*http://security.ubuntu.com/ubuntu*]("http://security.ubuntu.com/ubuntu")* natty-security main restricted*
*deb *[*http://security.ubuntu.com/ubuntu*]("http://security.ubuntu.com/ubuntu")* natty-security universe*
*deb-src *[*http://security.ubuntu.com/ubuntu*]("http://security.ubuntu.com/ubuntu")* natty-security universe*
*deb *[*http://security.ubuntu.com/ubuntu*]("http://security.ubuntu.com/ubuntu")* natty-security multiverse*
*deb-src *[*http://security.ubuntu.com/ubuntu*]("http://security.ubuntu.com/ubuntu")* natty-security multiverse*
*## Uncomment the following two lines to add software from Canonical's*
*## 'partner' repository.*
*## This software is not part of Ubuntu, but is offered by Canonical and the*
*## respective vendors as a service to Ubuntu users.*
*# deb *[*http://archive.canonical.com/ubuntu*]("http://archive.canonical.com/ubuntu")* natty partner*
*# deb-src *[*http://archive.canonical.com/ubuntu*]("http://archive.canonical.com/ubuntu")* natty partner*
*## This software is not part of Ubuntu, but is offered by third-party*
*## developers who want to ship their latest software.*
*deb *[*http://extras.ubuntu.com/ubuntu*]("http://extras.ubuntu.com/ubuntu")* natty main*
*deb-src *[*http://extras.ubuntu.com/ubuntu*]("http://extras.ubuntu.com/ubuntu")* natty main*
 
[/INDENT]Any help is much appreciated thanks.
 
Clement

---

### Post by jerrrys on 2011-07-20
change your server (software source) to main or use the "find best server" option and see if that works

---

### Post by clement_911 on 2011-07-20
Thanks for the answer.
I'm not very familiar with the Linux world.
Can you tell me how I do that ?

---

### Post by drs305 on 2011-07-20
> **clement_911 said:**
> Thanks for the answer.
I'm not very familiar with the Linux world.
Can you tell me how I do that ?
Open Synaptic (Home button upper left, start typing 'Synaptic' and the icon will appear): Settings > Repositories: Ubuntu Software tab. In the lower panel: Download From: Click on the existing server and a window will open. You can select one of the ones displayed or click 'Other' to see the complete list or "Choose Best Server".

You can access the same screen from Software Sources (the settings monitor in the lower left corner), or run:
```
sudo software-properties-gtk
```
If you use the command line, you will be asked for your password. Type your normal password and press ENTER. You won't see the characters as you type.

---

### Post by clement_911 on 2011-07-21
I chose best server and it ran 168 tests. Finally it showed a dialog saying "No suitable download server was found, Please check your internet connection".
My connection is definitely working in Firefox !

ps: I run the machine in a Virtual Box VM, would that matter that is connected to the same network as the host machine.

---

### Post by clement_911 on 2011-07-21
By the way. Ping works fine in the shell and my http_proxy variable is set...

---

### Post by jerrrys on 2011-07-21
just try setting it to "server for united states"

---

### Post by clement_911 on 2011-07-21
It still doesn't connect.

---

