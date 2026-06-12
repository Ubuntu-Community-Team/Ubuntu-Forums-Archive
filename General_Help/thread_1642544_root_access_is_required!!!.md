---
title: "root access is required!!!"
date: 2010-12-10
forum: General Help
---

### Post by thexnightmare on 2010-12-10
Dear,
I am traying to install an application on ubuntu, it asks me that I have to get root access.
How can I get this previlige?
Thx

---

### Post by Manyette on 2010-12-10
If installing from the command line, preface the command with sudo.  i.e. apt-get install <program>, and enter the admin password when prompted.  (It will not appear when you type it!)

---

### Post by Enigmapond on 2010-12-10
> **thexnightmare said:**
> Dear,
I am traying to install an application on ubuntu, it asks me that I have to get root access.
How can I get this previlige?
Thx

What are you trying to install and how??

---

### Post by thexnightmare on 2010-12-10
I am trying to install vmware, not from terminal. any idea?

---

### Post by Manyette on 2010-12-10
See this thread:  [https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

---

### Post by Enigmapond on 2010-12-10
> **thexnightmare said:**
> I am trying to install vmware, not from terminal. any idea? 

Can you give the scenario on what you've done, what kind of file you are attempting to install, what type of machine?? Distro??...and when does is ask for root access....you may just need to make it executable. Sounds like a permission thing. Also why VmWare?? The more information you give, the better the answer :D

---

### Post by thexnightmare on 2010-12-10
I am trying to install VMware Workstation 7 Linux x64. not server on ububutu 10.
I ahave file VMware-Workstation-7.0.0-203739.x86_64.bundle, when clicking on it, it told me that I have to get root access to be able to install it

---

### Post by tad1073 on 2010-12-10
open a terminal>cd into the directory where the .bundle file lives>type sudo ./VM then hit the tab key for auto completion>hit enter>then follow the instructions

---

### Post by thexnightmare on 2010-12-10
Sory but can u give me full line command to go to desktop in terminal? as I am new to this

---

### Post by thexnightmare on 2010-12-10
Thx solved

---

