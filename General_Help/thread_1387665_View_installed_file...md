---
title: "View installed file.."
date: 2010-01-22
forum: General Help
---

### Post by murali9181 on 2010-01-22
Hi all..
               I had installed ns-2.33 on ubuntu 9.04 using synaptic package manager. Now i need to edit routing protocol file in the Ns 2 folder. Wheni search for that file its not available but the installation is successfull. Can any one help me in this??

---

### Post by timgood on 2010-01-22
Try running 

sudo updatedb

in terminal and then searching again. Hope this helps.

---

### Post by sisco311 on 2010-01-22
> **murali9181 said:**
> Hi all..
               I had installed ns-2.33 on ubuntu 9.04 using synaptic package manager. Now i need to edit routing protocol file in the Ns 2 folder. Wheni search for that file its not available but the installation is successfull. Can any one help me in this??

I don't know what ns-2.33 is, but can list the files installed by a package with the:
```
dpkg -L package-name
```
command.

---

