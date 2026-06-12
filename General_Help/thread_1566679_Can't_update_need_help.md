---
title: "Can't update need help"
date: 2010-09-02
forum: General Help
---

### Post by BigCityCat on 2010-09-02
I am getting an error. I can't use synaptic, or update manager. When I try to remove the suspect package with sudo apt-get remove icogen. I get the following error.

> dpkg: error processing icogen (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 icogen
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by colobix on 2010-09-02
GO to synaptic > Edit > Repair broken packages.
You can also do this from recover mode.

---

### Post by BigCityCat on 2010-09-02
yeh I tried that it won't work. I navigated to where the program is supposed to be and its not there. It no longer resides in the menu either. When I goto synaptic it's marked for removal but will not allow me to unmark it or remove it. The computer janitor started this problem. 

I tried removing from recovery mode as well. This program I think has been removed but for some reason the system is continuing to try and remove it but can not find it.

---

### Post by BigCityCat on 2010-09-02
this program was a deb package I installed and then the computer janitor tried to remove but couldn't completely remove. 

To fix my problem I downloaded it again and it wouldn't let me reinstall it but I extracted it, copied the program file and pasted it using gksudo nautilus. Then I removed it with sudo apt-get remove and it found the program (that was actually gone) and removed it. That fixed the problem.

---

