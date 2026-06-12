---
title: "Frostwire OR something equivalent"
date: 2012-01-21
forum: General Help
---

### Post by brain7734 on 2012-01-21
I installed frostwire, but there were problems. I tried to uninstall it thru the terminal with 'sudo apt-get remove frostwire'. I try to install a different version of frostwire, but the original version I downloaded seems to stay. Can anyone tell me how to **COMPLETELY **remove it, or if there is something equivalent thru the free apps. Any help will be cool!!

---

### Post by imachavel on 2012-01-21
I don't know I just downloaded and installed it right now. After it installs I'll try sudo apt-get remove frost wire and see if it uninstalls

---

### Post by imachavel on 2012-01-21
worked for me:

sudo apt-get remove frostwire
[sudo] password for *****: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  frostwire
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 19.6 MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 270227 files and directories currently installed.)
Removing frostwire ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for hicolor-icon-theme ...


the package is still there so I have the option to reinstall it if I want. I don't know what to say. Have you tried using synaptic package manager, to uninstall and delete installer?

[http://maketecheasier.com/remove-repositories-in-ubuntu/2010/05/27](http://maketecheasier.com/remove-repositories-in-ubuntu/2010/05/27)

I'm going to have to memorize that page. I've been needing that help for awhile.

---

### Post by layers on 2012-01-21
the following will remove any config files
```
sudo apt-get purge frostwire
```

I use to use Nicotine, with no problems, as far as I remember.

---

### Post by brain7734 on 2012-01-21
Thanks, layers. This worked!!

---

### Post by |{urse on 2012-01-21
Or

sudo apt-get install murmur

another slsk client

---

