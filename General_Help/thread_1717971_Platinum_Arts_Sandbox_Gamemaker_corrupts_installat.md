---
title: "Platinum Arts Sandbox Gamemaker corrupts installation"
date: 2011-03-30
forum: General Help
---

### Post by Josh 443 on 2011-03-30
I have tried installing Platinum Arts Sandbox Gamemaker on 2 different computers, and both times, it stopped installing after about 90% of the installation. It just pauses and stops moving. When I go into recovery mode, It seems that it goes into an endless loop of attempting to fix it. It gets an error at the end of repairing it. The error code was (1). It then restarts the loop. When I restart Ubuntu and try to use the program, it tries to go into full screen mode, but quickly exits. When I try to uninstall it, The status bar just stays there at 0% and says applying changes, but does not move. I can still use Ubuntu, but when I try to update, it will only do a partial update. If it helps, I have tried installing it with both the 32-bit, and the 64-bit. How can I restore Ubuntu to before I tried to install the package? Or do I have to reinstall ubuntu.:?:

---

### Post by Josh 443 on 2011-03-31
When i tried to update Ubuntu 10.10, I get this error

Not all updates can be installed

Run a partial upgrade, to install as many updates as possible

This can be caused by:
*A previous upgrade which didn't complete
*Problems with some of the installed software
*Unofficial software packages not provided by Ubuntu
*Normal changes of a pre-release version of Ubuntu

it then has the option of a Partial Upgrade and to Close it. When I click close I get a box that says this:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Wen I run it, I get this error:

E: Invalid operation install-f



How do I fix this?

---

### Post by Josh 443 on 2011-03-31
I did "sudo apt-get remove sandboxgamemaker".
it seems to have removed it. I got this:

```
josh@josh-JR:~$ sudo apt-get remove sandboxgamemaker
[sudo] password for josh: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.35-22-generic linux-headers-2.6.35-22
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  sandboxgamemaker
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 9,855kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 187944 files and directories currently installed.)
Removing sandboxgamemaker ...
Processing triggers for menu ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Processing triggers for python-support ...
josh@josh-JR:~$ 

```

did it really remove it?

---

### Post by pearsy99 on 2012-01-31
I can confirm that this (sudo apt-get uninstall sandboxgamemaker) removed platinum arts sandbox gamemaker from my xubuntu 11.10

---

