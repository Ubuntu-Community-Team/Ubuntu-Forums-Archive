---
title: "confusing error message"
date: 2012-02-24
forum: General Help
---

### Post by Airycat on 2012-02-24
I;n trying to install Wallch on my mom's computer and get the following message.
> File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 968, in simulate
    trans.unauthenticated = self._simulate_helper(trans)
  File "/usr/lib/python2.7/dist-packages/aptdaemon/worker.py", line 1092, in _simulate_helper
    return depends, self._cache.required_download, \
  File "/usr/lib/python2.7/dist-packages/apt/cache.py", line 235, in required_download
    pm.get_archives(fetcher, self._list, self._records)
SystemError: E:I wasn't able to locate a file for the ttf-mscorefonts-installer package. This might mean you need to manually fix this package.
I have no clue what to do

Also... I was wondering if it might be related... frequently the fonts on her screen are cut in half. "o's" look like carets, so do "n's". The problem comes and goes. Could it be connected to the above error message (caused by the same problem)? If not, I'll repost separately.

---

### Post by enjoijesus94 on 2012-02-24
sudo apt-get install -f 

and see if that helps

---

### Post by enjoijesus94 on 2012-02-24
Or 
sudo dpkg --configure

---

### Post by dcstar on 2012-02-24
> **Airycat said:**
> **I'm trying to install Wallch** on my mom's computer
..........
[B]
Exactly[/B] how?

---

### Post by enjoijesus94 on 2012-02-24
Open A Terminal 
Applications > Accessories > Terminal

and copy paste the commands within the terminal

sudo dpkg --configure

or

sudo apt-get install -f 
im thinking your new to linux huh?:popcorn:

---

