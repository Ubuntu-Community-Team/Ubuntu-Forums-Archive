---
title: "Linux registry"
date: 2010-09-19
forum: General Help
---

### Post by anirudhtomer on 2010-09-19
hi all,

I am trying to make an application which finds the software capability of a LINUX system.

So if on a system some application can play ".avi" files my Software should tell which application on the system will run ".avi" files. 

In windows I can find the list of all extensions & corresponding applications (which run them) in REGISTRY.

I have read many posts while searching for some equivalent of Windows Registry in Linux.The replies on those posts were mostly saying that /etc folder has all configuration files, but my Aim is to find the list of all installed applications & the corresponding extensions they can play.

I have even run the command```
sudo gconf-editor
```.
Though the output the above command had a Node with name "apps" under which all applications were listed but it was not mentioned which extension each application can play.

Please help me out. Thanks in advance.

---

### Post by Rubi1200 on 2010-09-19
There is no equivalent of the Windows registry in Linux.

For information on where different things are placed in the file-system see here:
[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)

---

### Post by anirudhtomer on 2010-09-19
> **Rubi1200 said:**
> There is no equivalent of the Windows registry in Linux.

For information on where different things are placed in the file-system see here:
[http://www.thegeekstuff.com/2010/09/linux-file-system-structure/](http://www.thegeekstuff.com/2010/09/linux-file-system-structure/)
Thanks for the reply,

The link that you suggested was giving information on the FILE SYSTEM HIERARCHY.

I am trying to find a way to know the list of installed applications and the extension they can run.

---

### Post by ubun2warrior on 2010-09-19
u can find the installed applications in /usr/share/applications

regard 
ubun2warrior

---

### Post by anirudhtomer on 2010-09-19
> **ubun2warrior said:**
> u can find the installed applications in /usr/share/applications

regard 
ubun2warrior
thanks a lot. Your reply solved my problem.

---

