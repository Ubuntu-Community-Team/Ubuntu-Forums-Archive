---
title: "Error While Installing Wine"
date: 2010-07-04
forum: General Help
---

### Post by Honey_HR on 2010-07-04
[SIZE="5"]**Hello all, I am newbie to ubuntu and while installing wine,i got these problems, i don't know what to do please HELP, See the image below please**[/SIZE]
[img]http://gfxbucket.net/images/screenhuh.png[/img]]

[COLOR="Red"][SIZE="5"]Don't know what to do, HELP ME GUYS[/SIZE][/COLOR]

---

### Post by ronnielsen1 on 2010-07-04
Try to logout and log back in and see if that fixes it. I assume you onlu have one package manager open

---

### Post by krishnandu.sarkar on 2010-07-04
You're already using update manager / synaptic or apt to install / update something. You can install one at a time. So complete the existing one and try to install wine again. If you can't seem anything about this just try what ronnielsen1 said.

---

### Post by ajgreeny on 2010-07-04
This seems to have been caused more in the past year or so because the update manager opens but stays minimised, so users don't always realise it is open.  I have changed the action of my system back to what was the default, ie just show an icon when updates are available and not open the application itself, which you can also do, if you wish, by using gconf-editor->apps->update-notifier, and removing the tick from auto_launch.  See screenshot.

Open gconf-editor from the Alt+F2 dialog by typing **gconf-editor** in the box.

---

### Post by gadolinio on 2010-07-04
> **ronnielsen1 said:**
> Try to logout and log back in and see if that fixes it.
+1, that might be a good way to start if you don't know how to look for and end other processes.
As soon as you log in, try to install wine again.

---

### Post by Honey_HR on 2010-07-05
> **ajgreeny said:**
> This seems to have been caused more in the past year or so because the update manager opens but stays minimised, so users don't always realise it is open.  I have changed the action of my system back to what was the default, ie just show an icon when updates are available and not open the application itself, which you can also do, if you wish, by using gconf-editor->apps->update-notifier, and removing the tick from auto_launch.  See screenshot.

Open gconf-editor from the Alt+F2 dialog by typing **gconf-editor** in the box.

Thnks guys,
But what about "aptitude" and "synaptic" ??
And here is also a another problem
See the image below please

---

### Post by philinux on 2010-07-05
Use this command in the terminal.

```
sudo dpkg --configure -a
```

---

### Post by Kumar249kj on 2012-09-21
installArchives() failed: perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
perl: warning: Setting locale failed. 
perl: warning: Please check that your locale settings: 
    LANGUAGE = (unset), 
    LC_ALL = (unset), 
    LANG = "en_IN.ISO8859-1" 
    are supported and installed on your system. 
perl: warning: Falling back to the standard locale ("C"). 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Selecting previously unselected package cli-common. 
(Reading database ...  (Reading database ... 5%% (Reading database ... 10%% (Reading database ... 15%% (Reading database ... 20%% (Reading database ... 25%% (Reading database ... 30%% (Reading database ... 35%% (Reading database ... 40%% (Reading database ... 45%% (Reading database ... 50%% (Reading database ... 55%% (Reading database ... 60%% (Reading database ... 65%% (Reading database ... 70%% (Reading database ... 75%% (Reading database ... 80%% (Reading database ... 85%% (Reading database ... 90%% (Reading database ... 95%% (Reading database ... 100%% (Reading database ... 148341 files and directories currently installed.) 
Unpacking cli-common (from .../cli-common_0.8.2_all.deb) ... 
Selecting previously unselected package libmono-system-xml4.0-cil. 
Unpacking libmono-system-xml4.0-cil (from .../libmono-system-xml4.0-cil_2.10.8.1-1ubuntu2.2_all.deb) ... 
Selecting previously unselected package libmono-system-security4.0-cil. 
Unpacking libmono-system-security4.0-cil (from .../libmono-system-security4.0-cil_2.10.8.1-1ubuntu2.2_all.deb) ... 
Selecting previously unselected package libmono-system-configuration4.0-cil. 
Unpacking libmono-system-configuration4.0-cil (from .../libmono-system-configuration4.0-cil_2.10.8.1-1ubuntu2.2_all.deb) ... 
Selecting previously unselected package libmono-system4.0-cil. 
Unpacking libmono-system4.0-cil (from .../libmono-system4.0-cil_2.10.8.1-1ubuntu2.2_all.deb) ... 
Selecting previously unselected package libmono-security4.0-cil. 
Unpacking libmono-security4.0-cil (from .../libmono-security4.0-cil_2.10.8.1-1ubuntu2.2_all.deb) ... 
Selecting previously unselected package mono-4.0-gac. 
Unpacking mono-4.0-gac (from .../mono-4.0-gac_2.10.8.1-1ubuntu2.2_all.deb) ... 
Selecting previously unselected package mono-gac. 
Unpacking mono-gac (from .../mono-gac_2.10.8.1-1ubuntu2.2_all.deb) ... 
Selecting previously unselected package mono-runtime. 
Unpacking mono-runtime (from .../mono-runtime_2.10.8.1-1ubuntu2.2_i386.deb) ... 
Selecting previously unselected package libmono-corlib4.0-cil. 
Unpacking libmono-corlib4.0-cil (from .../libmono-corlib4.0-cil_2.10.8.1-1ubuntu2.2_all.deb) ... 
Selecting previously unselected package libmono-i18n4.0-cil. 
Unpacking libmono-i18n4.0-cil (from .../libmono-i18n4.0-cil_2.10.8.1-1ubuntu2.2_all.deb) ... 
Selecting previously unselected package libmono-i18n-west4.0-cil. 
Unpacking libmono-i18n-west4.0-cil (from .../libmono-i18n-west4.0-cil_2.10.8.1-1ubuntu2.2_all.deb) ... 
Processing triggers for man-db ... 
locale: Cannot set LC_CTYPE to default locale: No such file or directory 
locale: Cannot set LC_MESSAGES to default locale: No such file or directory 
locale: Cannot set LC_ALL to default locale: No such file or directory 
Processing triggers for desktop-file-utils ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf.index... 
Processing triggers for gnome-menus ... 
Setting up cogent-vdm (3.0.0) ... 
/opt/cogent/cogent-vdm/lib: 
    libv4l2uvc.so.0 -> libv4l2uvc.so.0.0.0 
    libCgtIrisAPI.so -> libCgtIrisAPI.so 
    libCG4EssentialsApi.so.0 -> libCG4EssentialsApi.so.0.0.0 
    libCG4IrisApi.so.0 -> libCG4IrisApi.so.0.0.0 
/var/lib/dpkg/info/cogent-vdm.postinst: 27: local: not in a function 
dpkg: error processing cogent-vdm (--configure): 
 subprocess installed post-installation script returned error exit status 2 
No apport report written because MaxReports is reached already
Setting up cli-common (0.8.2) ... 
Setting up libmono-security4.0-cil (2.10.8.1-1ubuntu2.2) ... 
Setting up mono-4.0-gac (2.10.8.1-1ubuntu2.2) ... 
Setting up mono-gac (2.10.8.1-1ubuntu2.2) ... 
update-alternatives: using /usr/bin/gacutil to provide /usr/bin/cli-gacutil (global-assembly-cache-tool) in auto mode. 
Setting up mono-runtime (2.10.8.1-1ubuntu2.2) ... 
update-alternatives: using /usr/bin/mono to provide /usr/bin/cli (cli) in auto mode. 
Setting up libmono-corlib4.0-cil (2.10.8.1-1ubuntu2.2) ... 
Setting up libmono-i18n4.0-cil (2.10.8.1-1ubuntu2.2) ... 
Setting up libmono-i18n-west4.0-cil (2.10.8.1-1ubuntu2.2) ... 
Setting up libmono-system4.0-cil (2.10.8.1-1ubuntu2.2) ... 
Setting up libmono-system-xml4.0-cil (2.10.8.1-1ubuntu2.2) ... 
Setting up libmono-system-security4.0-cil (2.10.8.1-1ubuntu2.2) ... 
Setting up libmono-system-configuration4.0-cil (2.10.8.1-1ubuntu2.2) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
Errors were encountered while processing: 
 cogent-vdm 
Setting up cogent-vdm (3.0.0) ... 
/opt/cogent/cogent-vdm/lib: 
    libv4l2uvc.so.0 -> libv4l2uvc.so.0.0.0 
    libCgtIrisAPI.so -> libCgtIrisAPI.so 
    libCG4EssentialsApi.so.0 -> libCG4EssentialsApi.so.0.0.0 
    libCG4IrisApi.so.0 -> libCG4IrisApi.so.0.0.0 
/var/lib/dpkg/info/cogent-vdm.postinst: 27: local: not in a function 
dpkg: error processing cogent-vdm (--configure): 
 subprocess installed post-installation script returned error exit status 2

---

### Post by Kumar249kj on 2012-09-21
> **philinux said:**
> Use this command in the terminal.

```
sudo dpkg --configure -a
```
I am getting error while executing above command

Setting up cogent-vdm (3.0.0) ...
/opt/cogent/cogent-vdm/lib:
    libv4l2uvc.so.0 -> libv4l2uvc.so.0.0.0
    libCgtIrisAPI.so -> libCgtIrisAPI.so
    libCG4EssentialsApi.so.0 -> libCG4EssentialsApi.so.0.0.0
    libCG4IrisApi.so.0 -> libCG4IrisApi.so.0.0.0
/var/lib/dpkg/info/cogent-vdm.postinst: 27: local: not in a function
dpkg: error processing cogent-vdm (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 cogent-vdm

---

### Post by Kumar249kj on 2012-09-21
hi,
I am using below command to install wine on my ubuntu 12 as root user

apt-get install wine

but i am getting below error.

Reading package lists... Done
Building dependency tree       
Reading state information... Done
wine is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 404 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up cogent-vdm (3.0.0) ...
/opt/cogent/cogent-vdm/lib:
    libv4l2uvc.so.0 -> libv4l2uvc.so.0.0.0
    libCgtIrisAPI.so -> libCgtIrisAPI.so
    libCG4EssentialsApi.so.0 -> libCG4EssentialsApi.so.0.0.0
    libCG4IrisApi.so.0 -> libCG4IrisApi.so.0.0.0
/var/lib/dpkg/info/cogent-vdm.postinst: 27: local: not in a function
dpkg: error processing cogent-vdm (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 cogent-vdm
E: Sub-process /usr/bin/dpkg returned an error code (1)


how can i resolve this error..?

i have also try below commands but i am failed.

dpkg -- configure -a
apt-get install winetricks
apt-get -f install winetricks
apt-get -f install wine

---

### Post by lisati on 2012-09-21
A lot can change in two years.

Old thread closed

---

