---
title: "Kaspersky How to remove?"
date: 2009-09-22
forum: General Help
---

### Post by churro on 2009-09-22
How do I remove  kaspersky rom my ubuntu jaunty completely? :confused:

---

### Post by wojox on 2009-09-22
Try:

```
dpkg --remove --force-remove-reinstreq kaspersky
```

---

### Post by churro on 2009-09-22
I tried what you said, It apperently is the correct way to uninstall it.

However, For some reason it just doesn't let me...  

Terminal gives me this message:



And Synaptic gives me this message:

Popup Window
E: kav4fs: subprocess pre-removal script returned error exit status 1


Details >


(Reading database ... 143028 files and directories currently installed.)
Removing kav4fs ...
Can't open perl script "/opt/kaspersky/kav4fs/lib/bin/setup/uninstall.pl": No such file or directory
dpkg: error processing kav4fs (--remove):
 subprocess pre-removal script returned error exit status 1
/var/lib/dpkg/info/kav4fs.postinst: 13: /etc/init.d/kavmidware: not found
update-rc.d: /etc/init.d/kav4fs: file does not exist
update-rc.d: /etc/init.d/kavmidware: file does not exist
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 kav4fs
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:


Such files do exist ~_~ I dunno what to do

---

### Post by Soul-Sing on 2009-09-22
You have to kill first all the karspersky proc.

---

### Post by churro on 2009-09-22
> **leoquant said:**
> You have to kill first all the karspersky proc.

no processes to kill.



But!  I got it removed, For some reason.... whatever reason that maybe

the actual folder in the .deb used to install kaspersky had a different folder name than the one installed in my /opt/

kav4fs
kav4ws

I renamed it to kav4fs and bingo! it removed via synaptic.

I  reinstalled it and the deb installed the folder (kav4ws) and i tried to uninstall it and error,  I renamed it again to (kav4fs) and it uninstalled it.


Well, Thanks to you all for trying to help me :)

---

