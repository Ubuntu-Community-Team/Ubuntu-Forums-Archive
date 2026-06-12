---
title: "Help!!!!!!!!"
date: 2009-10-02
forum: General Help
---

### Post by meluzi02 on 2009-10-02
I have a big problem right now..

what happened was that i have updated manager but before it has to be completed, someone restarted my pc and the process was corrupted...and i am trying to re-update manager but some error occur...

E: linux-image-2.6.28-15-generic: subprocess post-installation script returned error exit status 10
E: samba-common: subprocess post-installation script returned error exit status 10
E: smbclient: dependency problems - leaving unconfigured
E: libpam-smbpass: dependency problems - leaving unconfigured
E: samba: dependency problems - leaving unconfigured

please please i really need your help...

---

### Post by juancarlospaco on 2009-10-02
system--->administration--->synaptic

custom filters button--->broken--->remove all broken

update your system and reboot

---

### Post by meluzi02 on 2009-10-02
I have tried that one but when i click the broken button, it says that "no package is selected"

---

### Post by MaxIBoy on 2009-10-02
This is probably an easy fix.

Move the file /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst to your home folder. You will need to use sudo, as in ```
sudo mv /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst /home/$USER
``` ($USER is automatically substituted for the current username.) This is like deleting the file, except that this way you can restore it later if it turns out to be important. 

Sudo runs a single command with "root" (AKA "super user") privileges. Only use it for a single command at a time, where you understand what the command is going to do. In this case "mv" means "move." You call it as ```
mv   thing/you/want/to/move   place/you/want/to/move/it/to. 
```

Anyway, after you've done that command, you can try to finish the update. Post here if it doesn't work! And don't delete that postinst file until you're absolutely sure that the issue is resolved!

---

### Post by meluzi02 on 2009-10-02
honestly i did not understand the second code....sorry

can you please give an example...

---

### Post by MaxIBoy on 2009-10-03
The second one wasn't something you were supposed to run, I was explaining how the mv command works. (If you already know how it works, I apologize, but I like to explain these things in case people don't.) The ```
sudo mv /var/lib/dpkg/info/linux-image-2.6.28-15-generic.postinst /home/$USER
```one was what I was suggesting you actually run.

You can get a detailed explanation of the mv command here:
[http://linuxcommand.org/lts0050.php#mv](http://linuxcommand.org/lts0050.php#mv)

---

