---
title: "Problem removing bnetd..."
date: 2009-07-06
forum: General Help
---

### Post by Bill Zimmerly on 2009-07-06
I can't seem to be able to get rid of this program using Synaptic Package Manager. Here are the error details...

(Reading database ... 658184 files and directories currently installed.)
Removing bnetd ...
Stopping Battle.net(R) gaming server: invoke-rc.d: initscript bnetd, action "stop" failed.
dpkg: error processing bnetd (--purge):
 subprocess pre-removal script returned error exit status 1
chown: cannot access `/var/run/bnetd': No such file or directory
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bnetd
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

Thanks for any help!
- Bill

---

### Post by Bill Zimmerly on 2009-07-06
Ooops, I forgot to search for an answer before posting. :oops:

This thread provides an answer...

[http://ubuntuforums.org/showthread.php?t=777482&highlight=bnetd](http://ubuntuforums.org/showthread.php?t=777482&highlight=bnetd)

---

