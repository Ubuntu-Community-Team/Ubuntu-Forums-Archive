---
title: "cannot change permissions to execute file"
date: 2010-09-26
forum: General Help
---

### Post by techn0scho0lbus on 2010-09-26
Hi, im trying to execute a file. When I try i get the message:

The file ...Installer.exe is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run...

So when I right click on the file and select properties>permissions and check the 'allow executing file as program' it instantly unchecks the box. I can't check the box.

What's going on and how do i fix it?

---

### Post by Cavsfan on 2010-09-26
> **techn0scho0lbus said:**
> Hi, im trying to execute a file. When I try i get the message:

The file ...Installer.exe is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run...

So when I right click on the file and select properties>permissions and check the 'allow executing file as program' it instantly unchecks the box. I can't check the box.

What's going on and how do i fix it?

open terminal and navigate to where the file is and enter:
** sudo chmod +x <file-name>**

---

### Post by techn0scho0lbus on 2010-09-26
> **Cavsfan said:**
> open terminal and navigate to where the file is and enter:
** sudo chmod +x <file-name>**
Thank you. I am familiar with that command and understand it will solve my problem for the moment, but I would like to later use the GUI.  Is there a solution that can make the GUI work?

p.s. I already ran the program through the terminal I would just like to get this to function correctly.

---

### Post by lexfati on 2010-09-26
Just a head's up.  The .exe extension suggests that the file you are trying to run was written for Windows.  

Even if you add the permission to execute the file, you probably won't get what you want on a Linux system.  If there is a Linux version of the file available for download, you probably want to download that.

---

### Post by Cavsfan on 2010-09-26
> **techn0scho0lbus said:**
> Thank you. I am familiar with that command and understand it will solve my problem for the moment, but I would like to later use the GUI.  Is there a solution that can make the GUI work?

p.s. I already ran the program through the terminal I would just like to get this to function correctly.

Right click on the folder and click "open as administrator".
If you don't have that option, you can install Ubuntu Tweak, open it and go to the Nautilus settings and put a check mark by "open as administrator".

---

### Post by Cavsfan on 2010-09-26
> **lexfati said:**
> Just a head's up.  The .exe extension suggests that the file you are trying to run was written for Windows.  

Even if you add the permission to execute the file, you probably won't get what you want on a Linux system.  If there is a Linux version of the file available for download, you probably want to download that.

That's what I was thinking myself.

---

### Post by techn0scho0lbus on 2010-09-26
Thanks a lot^^ it's actually a game installer that i was trying to run with WINE =pp

---

### Post by vvoois on 2010-09-27
> **techn0scho0lbus said:**
> Thanks a lot^^ it's actually a game installer that i was trying to run with WINE =pp

Yeah, this file access permission policy is a real pain when you want to install wine related stuff...
Another ironic part of this is when you want to install stuff from cd, you can never set this execution bit, neither with chmod since CD's are read only. Any way to execute wine stuff from a console using kudo? (and also working?)
Why should cd's be untrusted in the first place anyway?

Not really cleverly thought through imho.

---

