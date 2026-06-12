---
title: "adobe causes crash, now mozilla won't work"
date: 2012-05-04
forum: General Help
---

### Post by oilspot on 2012-05-04
I kept gettting a crash report, it said that a third party application (adobe) was the problem. I tired to uninstall and it told me that packages were missing or something of the sorts. 

 Long story short. Another friend tried to help. He thought it would be a good idea to uninstall and reinstall firefox. Now Firefox is not accessable. The ubuntu software center says it's installed.   

 Where do I even start in getting this all working againg. At this point my computer is out of comission, and my wife and kids are pissed.

---

### Post by zombifier25 on 2012-05-04
Try starting Firefox in safemode in the terminal:
```
firefox -safe-mode
```

---

### Post by oilspot on 2012-05-04
i tried to start it in safe mode and it would not let me. It did give me a message that i could use;

sudo apt-get install firefox

I hoped maybe this would reinstall firefox and fix my problem. I didn't 
this is what i got:

garrett@garrett-desktop:~$ firefox -safe-mode
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox
garrett@garrett-desktop:~$ sudo apt-get install firefox
[sudo] password for garrett: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.32-34 linux-headers-2.6.32-34-generic python-smartpm
Use 'apt-get autoremove' to remove them.
Suggested packages:
  latex-xft-fonts firefox-gnome-support kmozillahelper
The following packages will be REMOVED:
  adobe-flashplugin
The following NEW packages will be installed:
  firefox
0 upgraded, 1 newly installed, 1 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B/16.8MB of archives.
After this operation, 22.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 322658 files and directories currently installed.)
Removing adobe-flashplugin ...
update-alternatives: error: no alternatives for iceape-flashplugin.
update-alternatives: error: no alternatives for iceape-flashplugin.
dpkg: error processing adobe-flashplugin (--remove):
 subprocess installed pre-removal script returned error exit status 2
postinst called with argument `abort-remove'
dpkg: error while cleaning up:
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 adobe-flashplugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
garrett@garrett-desktop:~$

---

