---
title: "cant erase synergy.conf"
date: 2011-05-08
forum: General Help
---

### Post by yogi1983 on 2011-05-08
Morning folks,
I'm  having a problem trying to uninstall Quicksynergy all the way.
first i did     sudo apt-get remove synergy
then sudo apt-get purge synergy
Checked in synaptic manager and software center that they did not show it. 

reinstalled synergy through the software center. and it is still showing me the name/ ip of my client.
so this tells me it did not uninstall everything.
i have searched the file system for synergy.conf with no luck
been high and low on the web but no luck.
any help would be great ,
thanks yogi

---

### Post by ajgreeny on 2011-05-08
Look in your home folder for hidden files and folders if you have not already done so.  Even using the purge option nothing from /home is removed and this can cause problems.

If you know for certain that the file you need to remove is called synergy.conf use the command ```
sudo updatedb && locate synergy.conf
```which will tell you if it really exists.

---

### Post by yogi1983 on 2011-05-09
thank you! i found the file and was able to get rid of it but still no synergy:(
thanks
yogi

---

