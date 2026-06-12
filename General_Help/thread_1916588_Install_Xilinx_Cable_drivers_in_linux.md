---
title: "Install Xilinx Cable drivers in linux"
date: 2012-01-28
forum: General Help
---

### Post by nuwan243 on 2012-01-28
Hi All; 
Im new to ubuntu. i have installed Xilinx web pack software.i want to run a JTAG programmer Cable(Xilinx Parallel Cable) with Xilinx web pack. For that its needed to install Cable drivers. i have downloaded them. when im installing them there is a error which is mention below

following you can see the command i gave and the output.Can any one help me to solve this. I think this is regarding permissions. Please help me Thank you

---------------------------------------------------------------------------------------------------------------------------
nuwan@nuwan-desktop:~/Desktop/install_drivers$ ls
install_drivers  linux_drivers  readme.txt
nuwan@nuwan-desktop:~/Desktop/install_drivers$ ./install_drivers
--Driver versions in this package: windrvr=900, xpc4drvr=1041
--Script name = ./install_drivers
--HostName = nuwan-desktop
--Current working dir = /home/nuwan/Desktop/install_drivers
--Script location = /home/nuwan/Desktop/install_drivers
--Kernel version = 2.6.31-14-generic.
--Arch = i686.
--Installer version = 1053
--Unsetting ARCH environment variable.
--User does not have root privileges.
--Module windrvr6 is not running.
--Module xpc4drvr is not running.
--Note: By default, the file permission of /dev/windrvr6 is enabled for the root user only
  and must be changed to allow access to other users.

--Return code = 2
nuwan@nuwan-desktop:~/Desktop/install_drivers$

---

### Post by Cheesemill on 2012-01-28
How about:
```
sudo ./install_drivers
```

---

