---
title: "Programming error in aptdaemon"
date: 2011-10-08
forum: General Help
---

### Post by mikhl on 2011-10-08
I am new to Ubuntu. 

I can not download anything from the software centre. I get the following error message.



Traceback (most recent call last): 
   File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate 
     trans.unauthenticated = self._simulate_helper(trans) 
   File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper 
     return depends, self._cache.required_download, \ 
   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download 
     pm.get_archives(fetcher, self._list, self._records) 
 SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


I am running Ubuntu 11.04

Please help me. Thanks

---

### Post by dcstar on 2011-10-08
> **mikhl said:**
> I am new to Ubuntu. 

I can not download anything from the software centre. I get the following error message.



Traceback (most recent call last): 
   File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 961, in simulate 
     trans.unauthenticated = self._simulate_helper(trans) 
   File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1085, in _simulate_helper 
     return depends, self._cache.required_download, \ 
   File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 226, in required_download 
     pm.get_archives(fetcher, self._list, self._records) 
 SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.


I am running Ubuntu 11.04

Please help me. Thanks

Find the **Synaptic** application and run that, it may allow you to find more information about the problem.

---

### Post by Krytarik on 2011-10-08
This should fix it:

[LIST=1]
[*]First, reboot your system, to make sure "dpkg" isn't locked.
[*]Run this command in the Terminal:```
sudo dpkg --configure -a
```
[*]Now you should get a confirmation dialog reg. the package "ttf-mscorefonts-installer"; press the Tab key to select <Ok>, and press Enter/Return to confirm it.
[/LIST]
Regards.

---

### Post by mikhl on 2011-10-09
> **dcstar said:**
> Find the **Synaptic** application and run that, it may allow you to find more information about the problem.

Thanks, I looked at the Synaptic application and updated apt. Seemed to do the trick. Though I must admit, I don't understand the problem, or why it needed updating :/

---

### Post by ankarajasekar on 2011-10-21
> **mikhl said:**
> Thanks, I looked at the Synaptic application and updated apt. Seemed to do the trick. Though I must admit, I don't understand the problem, or why it needed updating :/



sir  i use  11.10  i face the  problem  of   programming error in aptdaemon  how   to solve  the  issue  can u hjelp me
[email]ankarajasekar@gmail.com[/email]

---

