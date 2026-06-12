---
title: "cant uninstall kdebase-runtime-data"
date: 2010-08-01
forum: General Help
---

### Post by thingy87654321 on 2010-08-01
ok, so i was installing kget and i accedently turned off my computer while it was installing, kget is for KDE and since ubuntu uses gnome, it has to install the packages to make it work, one of which is kdebase-runtime-data

I cannot uninstall it through synaptic or terminal, i didnt uninstall kget, and thats the only KDE based app i have i think

I cannot install any apps because it is tring to remove kdebase-runtime-data even if i dont select it, its like always selected for removal and i cant uncheck it

I am running ubuntu 9.10 with the 2.6.31-22-generic kernel

Here is the output from terminal

aouate3@aouate3-laptop:~$ sudo apt-get remove kdebase-runtime-data
[sudo] password for aouate3: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  kdebase-runtime-data
0 upgraded, 0 newly installed, 1 to remove and 288 not upgraded.
1 not fully installed or removed.
After this operation, 8,495kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 153616 files and directories currently installed.)
Removing kdebase-runtime-data ...
dpkg (subprocess): unable to execute installed post-removal script: Exec format error
dpkg: error processing kdebase-runtime-data (--remove):
 subprocess installed post-removal script returned error exit status 2
Errors were encountered while processing:
 kdebase-runtime-data
E: Sub-process /usr/bin/dpkg returned an error code (1)
aouate3@aouate3-laptop:~$ 


is there a way to force this to be removed, or to get synaptic to ignore it, because i can no longer install anything :(

i spent the last couple days trying to install astaro security gateway on my desktop, only to relise my disk drive was failing and thats why it couldnt copy the packages, and after all that, ubuntu is doing this, almost enough to give me a brain aneurysm, and in fact it may have...

please help.... linux doesnt like me this week..... and i have been using linux for years and im not exactly a noob.... but this isnt something i have incountered before, stupid kde based apps ](*,)

---

### Post by thingy87654321 on 2010-08-01
Please help

---

