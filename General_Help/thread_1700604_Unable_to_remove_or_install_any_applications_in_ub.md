---
title: "Unable to remove or install any applications in ubuntu 10.10"
date: 2011-03-05
forum: General Help
---

### Post by irarum on 2011-03-05
I am unable to remove or install any applications using software centre or update manager or thru terminal. I have ubuntu 10.10 installed.This happened after i tried to install crossplatfromUI application for using Reliance Netconnect device.
The device is working without this file. I tried to use the janitor and Synaptic but does not work. 

I tried what was given [here]("http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1641387"). I am adding the text what i have got after trying some commands given in the thread.
```
sudo apt-get install -f
```
[sudo] password for murari: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  crossplatformui
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 127406 files and directories currently installed.)
Removing crossplatformui ...
ztemtvcdromd: no process found
dpkg: error processing crossplatformui (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 crossplatformui
E: Sub-process /usr/bin/dpkg returned an error code (1)
--------------
```
sudo dpkg --configure -a
```
----------------------------
```
sudo mkdir /var/cache/debconf
```
mkdir: cannot create directory `/var/cache/debconf': File exists
-------------------
```
sudo dpkg --configure -a
```
-------------------------
```
sudo service acpid restart
```
acpid start/running, process 2512
--------------------------------
```
sudo dpkg --configure -a
```
-------------------------------------
I also tried as beow nothing works

```
sudo dpkg -r crossplatformui 
```
[sudo] password for murari: 
(Reading database ... 127406 files and directories currently installed.)
Removing crossplatformui ...
ztemtvcdromd: no process found
dpkg: error processing crossplatformui (--remove):
 subprocess installed post-removal script returned error exit status 1
Errors were encountered while processing:
 crossplatformui

---------------------


Kindly help...
I am trying to learn Linux. 

Thanks

---

### Post by BigCityCat on 2011-03-05
I'm not sure if this will help but reboot and select recovery. Then select fix broken packages. See if that works.

---

### Post by irarum on 2011-03-05
there is no recovery option while doing a restart!!

---

### Post by BigCityCat on 2011-03-05
are you seeing the grub menu on restart? you could use the fix broken packages option in synaptic instead.

---

### Post by BigCityCat on 2011-03-05
goto synaptic. on the left look at custom filter. then select broken at the top.

---

### Post by Mark Phelps on 2011-03-05
> **irarum said:**
> there is no recovery option while doing a restart!!

You mean there's no GRUB menu, or there IS a GRUB menu but there is no Recovery option shown in that menu?

If there is no GRUB menu, hold down the SHIFT key when restarting.  That should force the display of a GRUB menu.

---

### Post by irarum on 2011-03-05
Tried to remove boken pakages through recovery mode.....
NO it does not work

the last line looks something like this

E: Sub-process /usr/bin/dpkg returned an error code (1)

---

