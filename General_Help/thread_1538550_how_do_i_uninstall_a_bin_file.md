---
title: "how do i uninstall a bin file"
date: 2010-07-25
forum: General Help
---

### Post by cranston on 2010-07-25
i have just installed the java run time environment (jre-6u21-linux-i586.bin) in the wrong directory on my desktop version of Ubuntu.  i wish to uninstall the files that are in the incorrect location and then  install these files in the correct directory (/usr/local/jrel.6.0_21).  i cannot remove the incorrectly located files.  the command rm -R does not work,  it claims that no such directory exists. the result of ls -l shop it to have the following permissions (drwxr-xr-x 8 root root       4096 2010-07-25 12:33 jre1.6.0_21).  i cannot change into the directory.  the lsattr attributes of the directory are --- ---  ---  ---.  i cannot move the directory and files as again the directory does not exist.

i have also used apt-get remove but still no success

the question is how do i uninstall this directory/files???

---

### Post by oldos2er on 2010-07-25
Where is the jre1.6.0_21 directory now? If it's not in your /home/user directory, you'll need to use **sudo rm -r /path/to/jre1.6.0_21**, for example. Or you can open Nautilus as root and delete from there (just be careful)with **gksu nautilus**.

---

