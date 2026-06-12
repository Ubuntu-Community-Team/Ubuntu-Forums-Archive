---
title: "List of packages from update manager!"
date: 2011-06-29
forum: General Help
---

### Post by EgoGratis on 2011-06-29
Is there a list of packages that come with regular Ubuntu updates  somewhere on the Internet? Or is there a command in the terminal to make such list. For example if i would like to see what was in Natty Narwhal updates 4 weeks back, how would i find that information

Thanks!

---

### Post by dabl on 2011-06-29
There is a log file at /var/log/dpkg.log that shows files installed during updates (or otherwise), as of the day you installed them.  Older logs are /var/log/dpkg.log.1, etc.

---

### Post by ajgreeny on 2011-06-29
If you use the update manager you can just open synaptic and go to File->History which lists everything that was installed or updated with both synaptic and the update manager.

If you use ```
sudo apt-get update
sudo apt-get upgrade
```you will have to use the log files mentioned by dabi.

---

### Post by EgoGratis on 2011-06-30
First of all thanks! I looked into it but there is one problem. This logs (dpkg) show everything? Not just updates but what i installed and uninstalled too? There really isn't a any web page with list and information about changes? Information that  you get in update manager about changes in the package and fixes? This is what i am after!

@ajgreeny i made some test now! Today i updated two packages with update manager and this was not loged in Synaptic -> File -> History. There are some logs in there for sure but very few of them and i think that all the logs of updating my system with update manager are not in there!

---

