---
title: "issues with uninstalling openjdk-6"
date: 2012-09-26
forum: General Help
---

### Post by NoonienSoong97 on 2012-09-26
I am trying to uninstall openjdk-6 so I can install jdk-6

I get this pop-up error:

Unhandable error occurred

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks. Please report this error at [http://launchpad.net/aptdaemon/+filebug](http://launchpad.net/aptdaemon/+filebug) and retry.

-> details
Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 779, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 958, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

I tried the launchpad site and wasn't able to fix the issue. I do know that I have to configure the dpkg, but I am not sure how to do that on the terminal.

---

### Post by QIII on 2012-09-26
This doesn't solve your immediate problem, but:

If you mean you want to uninstall OpenJDK to install Oracle Java, you don't need to.  Online tutorials that say that are simply incorrect.

Despite the fact that Oracle Java 7 has been found to be vulnerable to yet another attack, Oracle Java 6 is vulnerable to others.  You would be doing nothing more than trading sharks for alligators.  Oracle Java 6 and OpenJDK 6 will reach EOL in November.

If you must use Oracle Java, use Oracle Java 7 and make sure to set up an apparmor profile for Java to protect against this latest vulnerability if exploited.

To install Oracle Java 7, see the wiki in my signature.  Under "Oracle Java 7", "Command line methods" there is a link "Using webupd8.org's strikingly simple method".  That is by far the easiest way to install Java.

When Oracle puts out an update to fix this new vulnerability, you'll automatically get the update through the PPA during your normal Ubuntu updates.

As for your immediate problem, did you recently try to install the MS core fonts or ubuntu-restricted-extras?

---

