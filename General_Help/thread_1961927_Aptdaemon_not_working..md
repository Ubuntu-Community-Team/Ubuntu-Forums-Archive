---
title: "Aptdaemon not working."
date: 2012-04-20
forum: General Help
---

### Post by LorteMidget on 2012-04-20
When I try to install softare from Ubuntu Software Center, I get the following message:

There seems to be a programming error in aptdaemon, the software that  allows you to install/remove software and to perform other package  management related tasks.

Details : 

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre  package. This might mean you need to manually fix this package.

I don't know what to do here, and I have searched around the forums for some help, and I found some, but unfortunately it did not work.

Here is what I get:

Username:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock directory /var/lib/apt/lists/
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Username:~$ apt-get upgrade
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
Username:~$

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

As you can see I tried to use the following commands, but with no luck:

apt-get update
apt-get upgrade

What should I do?

---

### Post by plucky on 2012-04-20
> As you can see I tried to use the following commands, but with no luck:

apt-get update
apt-get upgrade

What should I do? 

Close all package managers/update manager and then use ```
sudo apt-get update
sudo apt-get upgrade
``` commands.

To fix the error try ```
sudo apt-get install -f
``` and post the output if there is an error.

You need to use sudo to give you the privilege to install software.


Good luck

---

### Post by LorteMidget on 2012-04-20
Thank you very much! Everything works fine now!

---

