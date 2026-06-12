---
title: "When I try installing ANY app from the Ubuntu Software centre I get an error"
date: 2011-10-25
forum: General Help
---

### Post by abhishek_turbo911 on 2011-10-25
[IMG]http://i52.tinypic.com/2qs6kur.png[/IMG]

This is the error that I get. Ubuntu 11.10

---

### Post by cryptotheslow on 2011-10-25
What does it say if you click where it says "Details" ?

---

### Post by abhishek_turbo911 on 2011-11-04
Copied from details:


Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.

---

### Post by plucky on 2011-11-04
> SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package. 

Open a terminal and run ```
sudo apt-get install -f
``` and post the output.

Good Luck

---

### Post by abhishek_turbo911 on 2011-11-04
I got this:

> 
abhishek@abhishek-laptop:~$ sudo apt-get install -f
[sudo] password for abhishek: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 83 not upgraded.



Actually, this was not the thing that I got the first time. When I ran your code, some true type installation came up in purple screen and to that I clicked "Do Not Agree" by mistake and it exited. But when I tried running your code again, hoping for that installation, I got the aforementioned message.

---

### Post by plucky on 2011-11-04
What does ```
sudo apt-get upgrade
``` now show you?

---

