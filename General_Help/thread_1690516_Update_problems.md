---
title: "Update problems"
date: 2011-02-18
forum: General Help
---

### Post by nnn= on 2011-02-18
For about a week, I've been having problems with updating adobe-flashplugin - I always get some error message. Well, now I have problems updating other packages. It says:

Requires installation of untrusted packages
The action would require the installation of packages from not authenticated sources.
adobe-flashplugin libssl-dev libssl0.9.8 login openssl passwd

---

### Post by sikander3786 on 2011-02-18
From Applications > Accessories > Terminal, just run this command.

```
sudo apt-get update
```

Your software index will be refreshed and I hope all will be well later.

---

### Post by nnn= on 2011-02-18
That fixed it mostly, except for adobe-flashplugin. It is still says:
Package operation failed
The installation or removal of a software package failed.

```
installArchives() failed: Preconfiguring packages ... 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 257279 files and directories currently installed.) 
Preparing to replace login 1:4.1.4.2-1ubuntu3 (using .../login_1%3a4.1.4.2-1ubuntu3.2_i386.deb) ... 
Unpacking replacement login ... 
Processing triggers for man-db ... 
Setting up login (1:4.1.4.2-1ubuntu3.2) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 257279 files and directories currently installed.) 
Preparing to replace libssl-dev 0.9.8o-1ubuntu4.3 (using .../libssl-dev_0.9.8o-1ubuntu4.4_i386.deb) ... 
Unpacking replacement libssl-dev ... 
Preparing to replace libssl0.9.8 0.9.8o-1ubuntu4.3 (using .../libssl0.9.8_0.9.8o-1ubuntu4.4_i386.deb) ... 
Unpacking replacement libssl0.9.8 ... 
Processing triggers for man-db ... 
Setting up libssl0.9.8 (0.9.8o-1ubuntu4.4) ... 
Processing triggers for libc-bin ... 
ldconfig deferred processing now taking place 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 257279 files and directories currently installed.) 
Preparing to replace passwd 1:4.1.4.2-1ubuntu3 (using .../passwd_1%3a4.1.4.2-1ubuntu3.2_i386.deb) ... 
Unpacking replacement passwd ... 
Processing triggers for man-db ... 
Setting up passwd (1:4.1.4.2-1ubuntu3.2) ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 257279 files and directories currently installed.) 
Preparing to replace adobe-flashplugin 10.1.102.65-2maverick1 (using .../adobe-flashplugin_10.2.152.27-0maverick1_i386.deb) ... 
Unpacking replacement adobe-flashplugin ... 
dpkg: error processing /var/cache/apt/archives/adobe-flashplugin_10.2.152.27-0maverick1_i386.deb (--unpack): 
 corrupted filesystem tarfile - corrupted package archive 
No apport report written because MaxReports is reached already
dpkg-deb: subprocess paste killed by signal (Broken pipe) 
postinst called with argument `abort-upgrade' 
dpkg: error while cleaning up: 
 subprocess installed post-installation script returned error exit status 1 
Preparing to replace openssl 0.9.8o-1ubuntu4.3 (using .../openssl_0.9.8o-1ubuntu4.4_i386.deb) ... 
Unpacking replacement openssl ... 
Preparing to replace telepathy-gabble 0.10.0-1 (using .../telepathy-gabble_0.10.0-1ubuntu0.1_i386.deb) ... 
Unpacking replacement telepathy-gabble ... 
Processing triggers for man-db ... 
Errors were encountered while processing: 
 /var/cache/apt/archives/adobe-flashplugin_10.2.152.27-0maverick1_i386.deb 
Setting up openssl (0.9.8o-1ubuntu4.4) ... 
Setting up telepathy-gabble (0.10.0-1ubuntu0.1) ... 
Setting up libssl-dev (0.9.8o-1ubuntu4.4) ... 
Setting up adobe-flashplugin (10.1.102.65-2maverick1) ... 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/iceape/plugins/flashplugin-alternative.so (iceape-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/iceweasel/plugins/flashplugin-alternative.so (iceweasel-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/mozilla/plugins/flashplugin-alternative.so (mozilla-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/firefox/plugins/flashplugin-alternative.so (firefox-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/xulrunner/plugins/flashplugin-alternative.so (xulrunner-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/midbrowser/plugins/flashplugin-alternative.so (midbrowser-flashplugin) in auto mode. 
update-alternatives: using /usr/lib/adobe-flashplugin/libflashplayer.so to provide /usr/lib/xulrunner-addons/plugins/flashplugin-alternative.so (xulrunner-addons-flashplugin) in auto mode. 

```

---

### Post by nnn= on 2011-02-19
Any ideas?

---

### Post by sikander3786 on 2011-02-19
Try these commands and post the complete outputs please.

```
sudo apt-get clean
sudo apt-get autoclean
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by slakkie on 2011-02-19
This seems to be your problem:

```


Unpacking replacement adobe-flashplugin ... 
dpkg: error processing /var/cache/apt/archives/adobe-flashplugin_10.2.152.27-0maverick1_i386.deb (--unpack): 
 corrupted filesystem tarfile - corrupted package archive 

```

sudo rm /var/cache/apt/archives/adobe-flashplugin_10.2.152.27-0maverick1_i386.deb 

and sudo aptitude install <the flashplugin package> should be enough to fix the glitch.

And key errors can be fixed like this:
[http://ubuntuforums.org/showthread.php?t=1291616](http://ubuntuforums.org/showthread.php?t=1291616)

---

### Post by nnn= on 2011-02-20
Removing the package fixed this issue.

---

