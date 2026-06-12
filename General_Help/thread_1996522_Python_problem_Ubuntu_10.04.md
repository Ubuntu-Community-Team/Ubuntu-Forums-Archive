---
title: "Python problem Ubuntu 10.04"
date: 2012-06-04
forum: General Help
---

### Post by BramWillemsen on 2012-06-04
Hi,

I currently have Ubuntu 10.04 installed on my office computer, and I tried to install a program called Mayavi2. When I try to run the program I get the following error: 

----------------------------------
Traceback (most recent call last):
  File "/usr/bin/mayavi2", line 25, in <module>
    import wxversion
ImportError: No module named wxversion

[4]+  Exit 1                  mayavi2
----------------------------------

I have both Python (2.6) and the python-wxversion packages installed in the software center. All the similar problems I found when googling dealt with users having 2 versions of Python installed, which is not the case here. I only have the Python from the software center installed. Could anyone please give me a suggestion?

Cheers

---

### Post by BramWillemsen on 2012-06-04
Could it be that the Python package is version 2.6.5-0ubuntu1 and the Python-wxversion package is 2.8.10.1-0ubuntu1.2 ? 

(some old forum post shows that the wxversion version does matter sometimes: [http://ubuntuforums.org/showthread.php?t=503538](http://ubuntuforums.org/showthread.php?t=503538) )

---

### Post by dino99 on 2012-06-04
this mayavi prog might need a specific package, maybe you can watch a readme or help file.

[https://launchpad.net/ubuntu/+source/wxwidgets2.8](https://launchpad.net/ubuntu/+source/wxwidgets2.8)

---

