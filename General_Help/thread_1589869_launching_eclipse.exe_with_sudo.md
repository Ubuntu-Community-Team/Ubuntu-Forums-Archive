---
title: "launching eclipse.exe with sudo"
date: 2010-10-07
forum: General Help
---

### Post by akash.mahakode@gmail.com on 2010-10-07
Hi All,

I have my eclipse folder, that contains eclipse.exe;
I am able to launch eclipse.exe by double clicking on it. 

But I want the following to be happened....
1. If I double click eclipse.exe, it should ask for sudo password, same as gksudo.

Please guide me to achieve this.


-akash

---

### Post by 3rdalbum on 2010-10-07
> **akash.mahakode@gmail.com said:**
> Hi All,

I have my eclipse folder, that contains eclipse.exe;
I am able to launch eclipse.exe by double clicking on it. 

But I want the following to be happened....
1. If I double click eclipse.exe, it should ask for sudo password, same as gksudo.

Please guide me to achieve this.


-akash

Why do you need Eclipse to run as root? The gksudo command does what you want, but it's a really bad idea to run anything as root if it doesn't need to.

---

### Post by akash.mahakode@gmail.com on 2010-10-07
Hi,

Thats true, but the code that I have return is responsible for mounting some drives from some other server to my machine. to mount and do some editing I must have sudo access. 
So, if i launch eclipse with sudo permissions, then i will mount the drives without user intervention.

-akash

---

### Post by ba_saish on 2010-10-08
you could create your own launcher. 
Righclick  on the Dektop and click on create launcher. 
Choose the appropriate application type and name for your launcher. 
In the command window, you can give sudo  <path to eclipse> 

This might solve your problem.

---

### Post by markh789 on 2010-10-08
SH Script?

Eclipse.sh
> 
gksudo path/to/the/eclipse.exe


Then just use the .sh script instead.

---

### Post by jespdj on 2010-10-08
Why are you trying to run eclipse.**exe**? That sounds like the Windows version of Eclipse (are you trying to run it via WINE?).

Why not just run the native Linux version of Eclipse?

---

### Post by shawinder on 2010-11-20
> **akash.mahakode@gmail.com said:**
> Hi All,

I have my eclipse folder, that contains eclipse.exe;
I am able to launch eclipse.exe by double clicking on it. 

But I want the following to be happened....
1. If I double click eclipse.exe, it should ask for sudo password, same as gksudo.

Please guide me to achieve this.


-akash

You can try ./eclipse command. Also make sure you have Java Run time installed

---

