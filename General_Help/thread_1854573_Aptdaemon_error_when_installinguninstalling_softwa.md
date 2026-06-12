---
title: "Aptdaemon error when installing/uninstalling software."
date: 2011-10-04
forum: General Help
---

### Post by thierrym89 on 2011-10-04
Whenever I try to remove/add software, I get the following error : 

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

Details : 

Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.


I am totally new to Linux, I tried searching to find a fix, but everybody seems to have different problems/solutions for aptdaemon problems, so I really don't know what to do...

Thanks!

---

### Post by dniMretsaM on 2011-10-04
Try this in terminal:
```
dpkg --configure -a
```

You might need to run that with root privileges (can't remember). If so, just use this:
```
sudo dpkg --configure -a
```

---

### Post by thierrym89 on 2011-10-04
I did it, it seemed to work fine (it didn't return any error message, just brought me back to the prompt), but I still have the exam same problem. Did I do something wrong? Was I supposed to be brought to some sort of configuration panel where I could have fixed it?

---

### Post by dniMretsaM on 2011-10-04
No, you did it right. I guess that wasn't the problem.

---

### Post by thierrym89 on 2011-10-04
Anybody else? :(

---

### Post by rsmatias on 2011-10-04
Try this on a terminal with root permissions:

apt-update
apt-upgrade

I've already experienced some problems when installing/uninstalling software. I solved it after making a general system upgrade. 

Maybe there were wrong package versions "trying" to work together.

Good luck!

regards,
RSM

---

### Post by thierrym89 on 2011-10-04
Are you working on a different shell than BASH? It doesn't found the command, and when I enter apt and type tab twice, it lists all the commands that start by apt, and there's nothing like upgrade or update...

---

### Post by rsmatias on 2011-10-04
Sorry, my mistake! Correct commands are:

apt-get update
apt-get upgrade

regards,
RSM

---

### Post by thierrym89 on 2011-10-04
Thanks a lot, that worked!

---

### Post by rsmatias on 2011-10-05
You welcome!!

I'm glad I could help you!

Regards,
RSM

---

### Post by feerdawooz on 2011-11-27
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
 what is this?? how to solve it??

---

### Post by feerdawooz on 2011-11-27
my problem is....

1st

i want to install open arena(first person shooting games) and playonlinux but when i hit my passwrod it cames like this:


E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

i can't do any updates or install.. plz help me..

2nd

when i try to clear cache,

it was same result


E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

what should i do??

---

### Post by K1ngchr15 on 2012-02-28
I know this post is a few months old now, but I used it just now when I had the same problem come up.

I input: 

apt-get update
apt-get upgrade

and I had the lock error aswell, so I ran it through root

:
sudo apt-get update
sudo apt-get upgrade

after that it did it's magic, I had to enter y for the upgrade, and then everything worked again. 

Hope this helps any other passers' by

---

