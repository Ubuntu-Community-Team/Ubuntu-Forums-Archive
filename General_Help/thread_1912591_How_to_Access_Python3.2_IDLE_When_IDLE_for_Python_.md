---
title: "How to Access Python3.2 IDLE When IDLE for Python 2.7 Still Installed?"
date: 2012-01-20
forum: General Help
---

### Post by tiansnake on 2012-01-20
Hi all!

I'm a beginner in both Ubuntu and Python. For some reason, I need to use the "urllib.request" module in python, which is not supported by Python2.x. So I installed Python3.2, but after typing "idle" in terminal, it seems that the old IDLE popped out again. And I still can't use urllib.request in the IDLE. Is it right in guessing that I need to link the shortcut-word "idle" to a newer version of IDLE? Any thought is really appreciated!

System: Ubuntu 11.04
Problem Description: Just downloaded and installed Python3.2, but kept Python2.7 on the computer still. Now I need to access the newer version of IDLE that comes with (does it really comes with Python3.2 or should I download a newer version of IDLE separately also?) python3.2. But in the terminal, if I type "idle", it jumps directly to the older version of IDLE (with following text displayed:"Python 2.7.1+ (r271:86832, Apr 11 2011, 18:05:24) 
[GCC 4.5.2] on Linux"). So my questions are:

1. If the newer version of IDLE is already installed together with Python3.2, how to access it? 
2. If I just type "idle" in the terminal, is this some kind of shortcut that links you directly to idle, saving the trouble of typing the entire file path? If so, how can I change the shortcut for "idle" from the older version IDLE to the newer version?  

Thank you for your time!

---

### Post by mwd5650 on 2012-01-20
I believe that IDLE is installed separate from base python3 you would need to install the idle3 package see [http://packages.ubuntu.com/oneiric/idle3]("http://packages.ubuntu.com/oneiric/idle3")

Matt

---

### Post by tiansnake on 2012-01-21
Thank you Matt! Problem solved taking your advice!

> **mwd5650 said:**
> I believe that IDLE is installed separate from base python3 you would need to install the idle3 package see [http://packages.ubuntu.com/oneiric/idle3]("http://packages.ubuntu.com/oneiric/idle3")

Matt

---

