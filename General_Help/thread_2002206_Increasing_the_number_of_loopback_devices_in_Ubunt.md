---
title: "Increasing the number of loopback devices in Ubuntu 12.04"
date: 2012-06-12
forum: General Help
---

### Post by Harsh Kumar Narula on 2012-06-12
Dear All,

I am trying to create local apt-repository on ubuntu 12.04, which needs mounting 11 iso images of the same by the following commands-

sudo mount /media/Stuffs/Precise\ Repo/ubuntu-12.04-repository-i386-**X**_contrib.iso /mnt/Repo**X** -o loop

Where: **X = 1 to 11**

What I get is that only 8 of them are mounted successfully as shown here

mount: warning: /mnt/Repo1 seems to be mounted read-only.
mount: warning: /mnt/Repo2 seems to be mounted read-only.
mount: warning: /mnt/Repo3 seems to be mounted read-only.
mount: warning: /mnt/Repo4 seems to be mounted read-only.
mount: warning: /mnt/Repo5 seems to be mounted read-only.
mount: warning: /mnt/Repo6 seems to be mounted read-only.
mount: warning: /mnt/Repo7 seems to be mounted read-only.
mount: warning: /mnt/Repo8 seems to be mounted read-only.
mount: could not find any free loop device  **(FOR REPO9)**
mount: could not find any free loop device  **(FOR REPO10)**
mount: could not find any free loop device  **(FOR REPO11)**

Seems number of loopback devices has to be increased. I tried many suggestion found by quick google search but nothing worked. 

Kindly help me !!! Thanks in advance. Pardon, my bad english :P. 

Harsh K. Narula

---

### Post by Harsh Kumar Narula on 2012-06-12
Problem is solved. [Mungwana]("http://ubuntuforums.org/member.php?u=901906")'s solution worked posted on [http://ubuntuforums.org/showthread.php?t=1375498](http://ubuntuforums.org/showthread.php?t=1375498).

---

