---
title: "Installation error - help me"
date: 2009-12-05
forum: General Help
---

### Post by shameedp on 2009-12-05
when i install any of my software i am getting this message
help me , what to do

E: The package adobe-flashplugin needs to be reinstalled, but I can't find an archive for it.

---

### Post by Leppie on 2009-12-05
Reinstall the flash plugin:
```
$sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
$sudo dpkg-reconfigure adobe-flashplugin --force
$sudo dpkg --purge --force-all adobe-flashplugin
$sudo apt-get install flashplugin-nonfree
```

---

### Post by shameedp on 2009-12-05
I try to delete these files
but i am not able to delete
sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
sudo dpkg-reconfigure adobe-flashplugin --force
sudo dpkg --purge --force-all adobe-flashplugin


I am getting command not found as error
i am not able to delete the files manually also
when i try to delete these files i am getting this message
 Unable to trash file: Permission denied

Please help me

---

### Post by shameedp on 2009-12-05
> **Leppie said:**
> Reinstall the flash plugin:
```
$sudo rm /var/lib/dpkg/info/adobe-flashplugin.prerm
$sudo dpkg-reconfigure adobe-flashplugin --force
$sudo dpkg --purge --force-all adobe-flashplugin
$sudo apt-get install flashplugin-nonfree
```

rm: cannot remove `/var/lib/dpkg/info/adobe-flashplugin.prerm': No such file or directory

---

### Post by shameedp on 2009-12-05
problem sovled

thanks for your kind help dude

can u tell me which download manager is best in ubuntu

---

### Post by Leppie on 2009-12-05
Glad it worked out. The error was because the dependencies file wasn't there, so it couldn't be deleted.

I don't really use any download manager. At times I download some torrents and am using Transmission. Wouldn't really be able to tell you what download manager to use, sorry bout that.

---

