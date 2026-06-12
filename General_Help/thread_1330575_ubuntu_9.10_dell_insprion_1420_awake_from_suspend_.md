---
title: "ubuntu 9.10 dell insprion 1420 awake from suspend no keyboard, mousepad use"
date: 2009-11-18
forum: General Help
---

### Post by seamles on 2009-11-18
Hi,

I've seen some posts on this before but haven't figured it out yet. 

I don't know how to edit the /etc/default/acpi-support file to change a line, how do I get root permission? 

or if there are other ways to fix this, I would be greatly appreciative! 

Any help is great, 

Hibernate has been fine but it's much slower than the suspend. 

Thanks

---

### Post by bertmanphx on 2009-11-18
seamles,
Unless you are comfortable modifying system files, I don't suggest you start with this one, and I don't know that this file exists, or would solve your problem.

However, to become "root", you need to use the "su" command from within a terminal.

bertmanphx

---

### Post by ajgreeny on 2009-11-18
> **bertmanphx said:**
> seamles,
Unless you are comfortable modifying system files, I don't suggest you start with this one, and I don't know that this file exists, or would solve your problem.

However, to become "root", you need to use the "su" command from within a terminal.

bertmanphx
No you don't.  Using the "su" command in ubuntu will do nothing.

You need to use "sudo" followed by whatever command you want to get root activities to work, eg ```
sudo nano install /etc/default/acpi-support
```or if you want to use gedit it is ```
gksudo gedit /etc/default/acpi-support
```
However this edit that you have no doubt seen elsewhere may or may not work, so don't be too disappointed if it doesn't.

---

### Post by bertmanphx on 2009-11-19
Oooops....sorry, he is correct.  I was just in my OpenSuSE installation :)

---

