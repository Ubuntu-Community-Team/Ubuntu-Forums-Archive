---
title: "[Errno 30] (read-only file system) when updating fresh 9.10 install"
date: 2010-01-18
forum: General Help
---

### Post by vekron on 2010-01-18
The following problem has happened to me several times over:

I install Ubuntu 9.10.  Everything works fine.
Then, I try to update the installation (I've tried both the GUI Update Manager and Aptitude).  It downloads all the packages, and even seems to install a few of them.  Then I get the following error:
```
Unpacking replacement gcalctool ...
Preparing to replace gdm 2.28.1-0ubuntu1

(gconftool 2.5256): GConf-WARNING **: Could not flush file '/var/lib/gconf/defaults/%gconf-tree-az.xml.new' to disk: Input/output error
Traceback: 
	*[...]*
OSError: [Errno 30] Read-only file system '/tmp/gconf/Vgz_BZ'
dpkg: warning: old pre-removal script returned error exit status 1
dpkg: - trying script from the new package instead
dpkg: ... it looks like that went OK.
dpkg: unrecoverable fatal error, aborting:
 unable to flush updated status of `gdm': Read-only file system
touch: cannot touch `/var/lib/update-notifier/dpkg-run-stamp': Read-only file system
E: Sub-process /usr/bin/dpkg returned an error code (2)
A package failed to install. Trying to recover:
dpkg: unable to access dpkg status area: Read-only file system
```

Then, the update process terminates.
At this point, the file system has become read-only (apparent from the error messages), and almost everything in the OS stops working; not even a halt/reboot command can be executed.

After a hard reboot, the OS fails to start up.  The first time around, it notices disk errors and asks me to run *fsck*, which I do, fixing the errors that it finds.  But after the next reboot, I don't even get as far as the command prompt.  The file system fails to mount.
(The same thing happens when trying to boot into recovery mode.)

At this point, with nothing working, I've tried reinstalling Ubuntu (more than once).  The same process repeats. (The only difference is that it may break at a different point in the update process - i.e., when installing something other than the gdm package.)

This is happening on a separate partition of my hard drive.  There are also two Windows partitions (NTFS), which seem unaffected: Windows boots without any problems.

Since this is happening to a fresh install, I'm kind of at a loss about what to do.  Any suggestions?

Thanks!

---

