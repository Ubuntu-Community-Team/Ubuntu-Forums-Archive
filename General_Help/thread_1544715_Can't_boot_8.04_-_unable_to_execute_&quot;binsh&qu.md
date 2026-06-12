---
title: "Can't boot 8.04 - unable to execute &quot;/bin/sh&quot; for rcS or rc-default - Help!"
date: 2010-08-02
forum: General Help
---

### Post by gkaucher on 2010-08-02
I am dual booting Ubuntu 8.04 and XP. I can boot into XP, but when I try to boot into 8.04 it gets past the splash screen and then stops with this message:

```
init: Unable to execute "/bin/sh" for rcS: No such file or directory
init: rcS main process (2622) terminated with status 255
init: Unable to execute "bin/sh" for rc-default: no such file or directory
init: rc-default main process (2623) terminated with status 255
```

Any ideas on how to fix this? I still have the installation CD for 8.04. Is there some way to use the CD to access the terminal on my hard drive installation, and if so, could I upgrade to 8.10 in the hopes that it would "repair" or reinstall /bin/sh?

Any ideas welcome.

---

### Post by gkaucher on 2010-08-06
I think that I deleted the /bin/sh directory. Is there any way to get it bacK.

---

### Post by gkaucher on 2010-08-08
This has been solved, but I'm not exactly sure what solved it.

First I booted with the LiveCD for Ubuntu 8.04 with the intention of copying all the files in the LiveCD's /bin directory and then pasteing them into the /bin folder on my hard drive's ubuntu 8.04 installation. This didn't work for two reasons:

1) I couldn't get permission to copy or paste
2) There was no /bin folder on my hard drive's ubuntu 8.04 installation

At this point I was trying different commands from the terminal that I saw in other posts, and I really don't think they changed anything.

Until I tried this: 

```
sudo nautilus 
seahorse nautilus module initialized
Initializing nautilus-share extension

** (nautilus:7011): WARNING **: Unable to add monitor: Operation not supported
```

This left me in a file management system that enabled me to first create a new /bin folder and then select, copy, and paste all of the files from the LiveCD's /bin directory into the /bin directory on my hard drive's ubuntu 8.04 installation.

After booting up, things seem to be working ok so far.

---

