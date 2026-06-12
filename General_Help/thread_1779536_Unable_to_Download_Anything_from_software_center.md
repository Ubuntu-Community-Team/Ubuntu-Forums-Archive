---
title: "Unable to Download Anything from software center"
date: 2011-06-10
forum: General Help
---

### Post by wizardduder on 2011-06-10
so i am unable to downlaod anything in the software center and here are the error messages

There seems to be a programming error in aptdaemon, the software that allows you to install/remove software and to perform other package management related tasks.

when i click on more info i get this
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the sun-java6-jre package. This might mean you need to manually fix this package.

please help its killing me not to be able to download things


so i found out that the sun-java6-jre package is bad in synaptic package manager and it wont let me remove it so how do i go about doing that

---

### Post by wizardduder on 2011-06-10
before i forget im using 11.04

---

### Post by sikander3786 on 2011-06-10
On Unity, press the <Super> (Windows logo key) and search for 'Terminal' or if regular Gnome session, go to Applications > Accessories > Terminal and run and post the outputs of these commands.

```
sudo dpkg --configure -a
sudo apt-get install -f
```

---

### Post by wizardduder on 2011-06-10
dpkg: error: dpkg status database is locked by another process
~$ sudo apt-get install -f
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?


i put in edit in my original post of someting i think would be useful and how do u get in that sweet box. but theres what it says back

---

### Post by sikander3786 on 2011-06-10
For the box you can click # icon in post menu and paste your text in between the generated [code] tags.

For the outputs, it says that some other package manager is running like Software Center, Update Manager or Synaptic. Please close the other one and run the commands again. If the output is still the same, log out and back in and perform the commands.

---

