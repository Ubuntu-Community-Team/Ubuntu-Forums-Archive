---
title: "How to create an icon at desktop for info utility"
date: 2010-09-28
forum: General Help
---

### Post by Like2Learn on 2010-09-28
I am running a virtual machine with Ubuntu via VMware Player at my Windows XP desktop.
 
Instead of running info utility from the terminal, I would like to run it from the GNOME desktop by double clicking. I first created an icon by using "create launcher...", then I fill "info" for Command. However, there is no response when I double-click this icon.
 
I also tried to type in "gksudo info" for Command, still no response. Anybody can help?
 
Thanks.

---

### Post by Like2Learn on 2010-09-28
> **Like2Learn said:**
> I am running a virtual machine with Ubuntu via VMware Player at my Windows XP desktop.
 
Instead of running info utility from the terminal, I would like to run it from the GNOME desktop by double clicking. I first created an icon by using "create launcher...", then I fill "info" for Command. However, there is no response when I double-click this icon.
 
I also tried to type in "gksudo info" for Command, still no response. Anybody can help?
 
Thanks.
 
BTW, I also tried "/usr/bin/info" and "/usr/bin/info/info", still 
doesn't work. 

user@ubuntu:~$ which info 
/usr/bin/info 
user@ubuntu:~$ whereis info 
info: /usr/bin/info /usr/share/info /usr/share/man/man1/info.1.gz /usr/ 
share/man/man5/info.5.gz

---

### Post by psusi on 2010-09-28
You might try installing emacs and using info within emacs.  I never use the standalone info viewer.

---

### Post by 3rdalbum on 2010-09-28
> **Like2Learn said:**
> I am running a virtual machine with Ubuntu via VMware Player at my Windows XP desktop.
 
Instead of running info utility from the terminal, I would like to run it from the GNOME desktop by double clicking. I first created an icon by using "create launcher...", then I fill "info" for Command. However, there is no response when I double-click this icon.

In the Create Launcher window, for the "Type", you need to choose "Application in Terminal" because *info* is a terminal program.

---

### Post by Like2Learn on 2010-09-29
> **3rdalbum said:**
> In the Create Launcher window, for the "Type", you need to choose "Application in Terminal" because *info* is a terminal program.
 
It works. Many thanks!

---

