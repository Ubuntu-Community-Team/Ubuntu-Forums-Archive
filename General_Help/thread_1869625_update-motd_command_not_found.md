---
title: "update-motd: command not found"
date: 2011-10-26
forum: General Help
---

### Post by wuhtzu on 2011-10-26
Hi everyone

I am using update-motd to update the motd (:P) and it works almost great. Just add new scripts to /etc/update-motd.d and they eventually show up in 10 minutes time upon login.

But I am not able to do manual updates using **update-motd --force**. I get the following error:

**update-motd: command not found**

According to the man page it should be possible ([http://manpages.ubuntu.com/manpages/jaunty/en/man1/update-motd.1.html](http://manpages.ubuntu.com/manpages/jaunty/en/man1/update-motd.1.html)). It would be very handy to be able to do this while setting up a new motd, so you don't have to wait 10min between seeing the results of your edits.

Any ideas?

Thanks,
Wuhtzu

---

### Post by dcstar on 2011-10-26
> **wuhtzu said:**
> Hi everyone

I am using update-motd to update the motd (:P) and it works almost great. Just add new scripts to /etc/update-motd.d and they eventually show up in 10 minutes time upon login.

But I am not able to do manual updates using **update-motd --force**. I get the following error:

**update-motd: command not found**

**According to the man page it should be possible **([http://manpages.ubuntu.com/manpages/jaunty/en/man1/update-motd.1.html](http://manpages.ubuntu.com/manpages/jaunty/en/man1/update-motd.1.html))
......


No, that man page is for (very) old Ubuntu versions, that package no longer exists.

The MOTD functions have been migrated into the PAM subsystem:

[http://packages.ubuntu.com/search?keywords=update-motd&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=update-motd&searchon=names&suite=all&section=all)

---

### Post by wuhtzu on 2011-10-26
Thanks for you reply dcstar. 

This brings me back to square one. I literally searched for hours for "pam_motd x" (with x = howto, tutorial, change, modify etc) and found no good references explaining how this works.

All I can see is that the scripts in /etc/update-motd.d/ is still used to produced the motd and I still see no way of manually forcing the motd to be updated while working on a new motd.

---

### Post by wuhtzu on 2011-10-27
However misleading naming of folders, services and so on it seems to just work.

Editing, removing and adding files in /etc/update-motd.d/ works and it works immediately. Change something, login again and the change is there.

Any preferred methods suppressing the output from scripts in the /etc/update-motd.d/ folder? You could of course hash (#) all lines in the unwanted files, simply delete the file or move it to "/etc/update-motd.d/unused-scripts/ or similar.

---

### Post by tkoco on 2011-11-12
Don't know about immediate fixes to the displayed motd, but if you have static info to be appended to the motd, just create a text file called
```
/etc/motd.tail
``` and it will be automatically recognized and added to the official motd.

---

