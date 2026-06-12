---
title: "ms true-type font error on 64 bit ubuntu 10.10"
date: 2011-01-09
forum: General Help
---

### Post by supasoaker on 2011-01-09
hi all, i tried to install microsoft true type fonts using apt-get first - the installation was stopped on a configuration part, the terminal turned into something that looked like a BIOS setup........it was the user agreement and I couldn't click <ok>............so i terminated the terminal session.........

then I tried the Software Center and started to install but it took ages, when I checked the In Progress tab it still hadn't started saying that it was trying to close apt-get...................

i cancelled and restarted............now it says the true-type fonts are installed but I can't use them, and cannot remove as I get errors:

**ttf-mscorefonts-installer**:

installArchives() failed: dpkg: error processing ttf-mscorefonts-installer (--remove): 
 Package is in a very bad inconsistent state - you should 
 reinstall it before attempting a removal. 

**ttf-liberation:**

Traceback (most recent call last):
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 768, in simulate
    return self._simulate_helper(trans, status_path)
  File "/usr/lib/python2.6/dist-packages/aptdaemon/worker.py", line 936, in _simulate_helper
    return depends, status, self._cache.required_download, \
  File "/usr/lib/python2.6/dist-packages/apt/cache.py", line 218, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.



Question is how do I manually fix any of this? Much obliged for ANY HELP!!!!

---

### Post by oldfred on 2011-01-09
Because the accept was in the terminal you could not use mouse but some combination of tab and enter seemed to work. I just start hitting keys as they often are not consistent.

I would do a full purge and reinstall. You should be able to do it from synaptic or :

apt-get update
apt-get upgrade

apt-get purge msttcorefont
apt-get install msttcorefont

---

### Post by supasoaker on 2011-01-10
thanks - i did apt-get update and then upgrade, there was alot to do since it was a fresh install (which might have cause some of the issue), in the middle of the upgrade the BIOS type terminal thing came up again..........so i proceeded (thanks to tab) and all is well now.

Much obliged!

---

