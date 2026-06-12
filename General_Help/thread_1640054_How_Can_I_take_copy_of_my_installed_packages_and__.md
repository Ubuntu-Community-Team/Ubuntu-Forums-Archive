---
title: "How Can I take copy of my installed packages and  backup my system ??"
date: 2010-12-07
forum: General Help
---

### Post by drdigital on 2010-12-07
Hello My Ubuntu colleagues ,
I want to know some thing here,
Every time I install ubuntu I have to reinstall all the software from the software center and so. Now I already installed all software I need for this moment. Is there a way to take source files of those (installed) packages and save them some where else in order to reinstall them if i needed next time without need to INTERNET connection ???

Another question I wanna know about: How can I take a backup of my system as whole in order to get back to it if some problem happened. I used to use Acronis True Image and its alternatives to make a disk image. Is there is some thing similar in linux ?? is there better options ??

Thank so much.
see u.

---

### Post by BlueSpecial on 2010-12-07
Try these steps:

[http://www.hanckmann.net/?q=node/19](http://www.hanckmann.net/?q=node/19)

---

### Post by HermanAB on 2010-12-07
Howdym

Since pretty much all settings are in /etc, all you need to do is make a tar ball of that for future reference.

---

### Post by azertyh on 2010-12-07
hello,
try [APTonCD](https://help.ubuntu.com/community/APTonCD).
or [this](http://ubuntuforums.org/showthread.php?t=819396).

---

### Post by oldfred on 2010-12-07
If your reinstall is a newer version you will want to reinstall the more up to date applications also. This just outputs a list of apps and will install the newer versions:

from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

 dpkg --get-selections | grep -v deinstall > ubuntu-files
or
 dpkg --get-selections > ubuntu-files


and using synaptic
[http://ubuntuforums.org/showthread.php?t=1057608](http://ubuntuforums.org/showthread.php?t=1057608)
File > Save Markings As, tick the "Save full state, not only changes". If you don't tick the 'full state', you will probably get an empty file.
To restore, you would use File, 'Read Markings'

For backup I just rsync my data (which is not in /home), /home and any system settings I know I changed in /etc. But do not restore all of /etc unless you have the same version as the settings may change and usually want the newer versions.

[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)
[http://www.rsnapshot.org/](http://www.rsnapshot.org/)
[http://backintime.le-web.org/](http://backintime.le-web.org/)

aptoncd 
Location of downloaded debs
/var/cache/apt/archives/

[http://clonezilla.org/](http://clonezilla.org/)
[http://www.geekconnection.org/remastersys/](http://www.geekconnection.org/remastersys/)
[http://www.psychocats.net/ubuntu/remastersys](http://www.psychocats.net/ubuntu/remastersys)

---

