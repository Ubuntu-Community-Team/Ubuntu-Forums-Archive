---
title: "possible workaround for repository/install-routine bug (regarding fuse-utils)"
date: 2010-02-07
forum: General Help
---

### Post by manolo_asdf on 2010-02-07
hi,

i want to install fuse-utils, but the install crashes. i read in [mailing-list entry]("http://www.mail-archive.com/debian-bugs-dist@lists.debian.org/msg568397.html"), that this seems to be a bug (though it is from 2008 and i wonder why it is still there...).

never the less i would like to install fuse-utils. what is the best way to workaround the install-routine problem?

thanks

log from install-routine:
```

root@v37013:/etc/cron.weekly# aptitude install fuse-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
The following partially installed packages will be configured:
  fuse-utils sshfs 
0 packages upgraded, 0 newly installed, 0 to remove and 83 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = "en_GB.UTF-8",
	LANG = "en_GB.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
locale: Cannot set LC_CTYPE to default locale: No such file or directory
locale: Cannot set LC_MESSAGES to default locale: No such file or directory
locale: Cannot set LC_ALL to default locale: No such file or directory
Setting up fuse-utils (2.7.4-1.1ubuntu4) ...
creating fuse group...
udev active, skipping device node creation.
 * Reloading kernel event manager...                                                                                                No /sbin/udevd found running; none killed.
                                                                                                                             [fail]
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing fuse-utils (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sshfs:
 sshfs depends on fuse-utils (>= 2.7); however:
  Package fuse-utils is not configured yet.
dpkg: error processing sshfs (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 fuse-utils
 sshfs
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up fuse-utils (2.7.4-1.1ubuntu4) ...
creating fuse group...
udev active, skipping device node creation.
 * Reloading kernel event manager...                                                                                                No /sbin/udevd found running; none killed.
                                                                                                                             [fail]
invoke-rc.d: initscript udev, action "reload" failed.
dpkg: error processing fuse-utils (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of sshfs:
 sshfs depends on fuse-utils (>= 2.7); however:
  Package fuse-utils is not configured yet.
dpkg: error processing sshfs (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 fuse-utils
 sshfs
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```

---

