---
title: "ANSYS installation in UBUNTU10.10"
date: 2011-06-16
forum: General Help
---

### Post by anshulfy on 2011-06-16
Hi,

I have Ubuntu10.10 in my HP-laptop. I am trying to install ANSYS. There is an INSTALL file in setup. When I try to give INSTALL in terminal, being in the same directory it says, command not found. I tried ./INSTALL, it says "bash: ./INSTALL: Permission denied". 
I also tried from my home folder with full path for the INSTALL file, as the readme file says, "To install, enter the full path to the installation program on the 
media or to the downloaded installation files".
I don't know what to do :( .I have these setup file in my external hard drive. Please help me.

Thanks in advance. 
--
Anshul

---

### Post by jake.anq on 2011-06-16
Hi

Try running
```
$sudo su -
```
and then retry ./INSTALL
This will run the program as root.

---

### Post by anshulfy on 2011-06-16
Thanks Jake,

I tried running it as a root. It still says, "-su: ./INSTALL: Permission denied".

---

### Post by jake.anq on 2011-06-16
Hi

Run 
```
sudo chmod 777 INSTALL
```
on the file then retry.  If you have the file on a USB with FAT, it may not work, in which case copy the entire directory to the hdd.

---

### Post by anshulfy on 2011-06-16
Thanks Jack, Its working on. I copied the setup files to hdd and then run the "sudo chmod  777 install" on install file. Then using ./INSTALL i was able to install.  Thanks a lot.

Could you please tell me, what was the problem? I am new to Linux. :).

--
Anshul

---

### Post by anshulfy on 2011-06-16
Hi,
I could install ansys. But stuck into a new problem. There are some post-installation procedure, before i could run it. These procedures are mentioned in the below link.

[http://www.kxcad.net/ansys/ANSYS/installs/Hlp_IN_UNIXPOST.html](http://www.kxcad.net/ansys/ANSYS/installs/Hlp_IN_UNIXPOST.html)

I am not getting anything out of it. It will be a great help it someone can explain in what I have to do.

--
Anshul

---

### Post by jake.anq on 2011-06-17
> **anshulfy said:**
> Thanks Jack, Its working on. I copied the setup files to hdd and then run the "sudo chmod  777 install" on install file. Then using ./INSTALL i was able to install.  Thanks a lot.

Could you please tell me, what was the problem? I am new to Linux. :).

--
Anshul
 
Hi

Ubuntu has a system of 'file permissions'
chmod 777 sets these permissions so that anyone can read, write or execute it.  For more info, [http://www.tuxfiles.org/linuxhelp/filepermissions.html](http://www.tuxfiles.org/linuxhelp/filepermissions.html)

---

