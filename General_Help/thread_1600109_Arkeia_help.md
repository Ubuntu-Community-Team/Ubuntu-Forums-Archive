---
title: "Arkeia help"
date: 2010-10-18
forum: General Help
---

### Post by rossiFan on 2010-10-18
Hello Everyone,
I have an Ubuntu Server 8.04 box using a licensed install of Arkeia to backup a remote office.  I'm posting here because I let my maint agreement with them lapse.  :-? I updated it last week (apt-get upgrade), and it updated my Arkeia config files, too.  It was at Arkeia 7.04.  Now, when I try to upgrade Arkeia, it's fine, but when I try to upgrade arkwui (the web interface portion), I get:
```
root@back-hou-01:~# dpkg -i arkeia.8.2.9_arkwui_linux.ubuntu8.04_x86.deb
(Reading database ... 50371 files and directories currently installed.)
Preparing to replace arkwui 8.2.9-1 (using arkeia.8.2.9_arkwui_linux.ubuntu8.04_x86.deb) ...
/var/lib/dpkg/info/arkwui.prerm: 22: /etc/init.d/arkwui: not found
Unpacking replacement arkwui ...
Setting up arkwui (8.2.9-1) ...
update-rc.d: /etc/init.d/arkwui: file does not exist
dpkg: error processing arkwui (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 arkwui

```

I have tried uninstalling the .deb, installing from repos, and I get the same error.  If I can just do a temp install of Arkeia, I can restore my old installation.  Any help would be awesome.

---

### Post by frenard on 2010-10-19
Hi RossiFan,

I am not a technical person but let me point out a possible reason of your issue.

It looks like that you own Arkeia licenses (you mentioned that you drop Arkeia maintenance). These commercial licenses work with the packages available from Arkeia download website.

Arkeia made available for free a non-time limited version of its Arkeia software to Ubuntu LTS users, available directly from Ubuntu's repository. However, commercial licenses cannot work on this specific version.

I am from Arkeia; I hope that we will have a chance in the future to get you back under maintenance ;)

In case you missed it, there is a [Wiki section dedicated to the Ubuntu Enterprise Backup]("http://wiki.arkeia.com/mediawiki/index.php/Ubuntu-Enterprise-Backup") version of Arkeia at: [http://wiki.arkeia.com/mediawiki/index.php/Ubuntu-Enterprise-Backup](http://wiki.arkeia.com/mediawiki/index.php/Ubuntu-Enterprise-Backup)

Cheers,

Frederic

---

### Post by rossiFan on 2010-10-19
That is what happened - when I upgraded, my version was replaced.  I downloaded the latest debs from Arkeia, and arkeia.8.2.9_master installs fine, but arkwui does not with the above error.

---

### Post by rossiFan on 2010-10-19
Got it - dpkg --purge on the violating arkwui package worked.  I was able to install it fine and got everything up and running with the help of:

[http://wiki.arkeia.com/mediawiki/index.php/Upgrade_Arkeia](http://wiki.arkeia.com/mediawiki/index.php/Upgrade_Arkeia)

---

