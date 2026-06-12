---
title: "Cannot remove/install VMware workstation"
date: 2011-05-09
forum: General Help
---

### Post by Morph-------------- on 2011-05-09
Hello,

I've been trying to install VMware workstation 7.1.4- but I've run into a problem. Due some bugs i've had to install vmware a couple of times. Now one time I removed /etc/vmware before uninstalling it. This might be stupid but after I've done this vmware wouldn't uninstall anymore. It would say that there where instances of vmware running though I've never even been at the point that I ran vmware. The installer would say that vmware was already installed so it wouldn't install either. Now I've removed as much vmware files as I could find. But now if I run ```
sudo sh vmware-workstation-full-7.1.4-385536.i386.bundle 
```
It wil say > Extracting VMware Installer...done.

And then nothing. It will just silently quit. It doesn't give an error, it doesn't start the installer GUI, it will just quit. Now I suspect there are vmware files somewhere that confuse the installer but I've no idea if this is true or where these files are. Does someone know how to completly wipe any vmware-workstation file from my computer as if vmware was never installed?

Thanks in advance

EDIT: if I run sh vmware-workstation-full-7.1.4-385536.i386.bundle -r, it will show the installer again but show that vmware is already installed

---

### Post by rhigmus on 2011-05-17
Try this since it's claiming that vmware is already installed

```
vmware-installer -l
```

should list any vmware products installed like so:

> 
Product Name           Product Version     
====================== ====================
vmware-workstation     7.1.0.261024 


if you get a result like that, try this to uninstall:

```
vmware-installer -u vmware-workstation
```

Just did this myself and it worked. However, I haven't been able to re-install successfully yet :(

It may be relevant to note that I just upgraded to 10.10 yesterday which resulted in the vmware break in the first place. recompiling modules just doesn't want to work.

---

