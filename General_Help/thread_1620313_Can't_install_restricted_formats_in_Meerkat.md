---
title: "Can't install restricted formats in Meerkat"
date: 2010-11-12
forum: General Help
---

### Post by Onoku on 2010-11-12
I tried to install them through the software center first. It would show "in progress" on the left hand side for a couple seconds and then it would go away, but the formats did not install. 

next I found a command to copy and paste, but it didn't work either

> mike@mike-MacBook:~$  $ wget -c [http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/multiverse/f/flashplugin-nonfree/flashplugin-nonfree_7.0.63.3ubuntu3_i386.deb)
$: command not found
mike@mike-MacBook:~$ 
mike@mike-MacBook:~$                    wget -c [http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb)
--2010-11-13 05:54:17--  [http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/g/gsfonts-x11/gsfonts-x11_0.17ubuntu4_all.deb)
Resolving archive.ubuntu.com... 91.189.88.40, 91.189.88.45, 91.189.88.46, ...
Connecting to archive.ubuntu.com|91.189.88.40|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 9402 (9.2K) [application/x-debian-package]
Saving to: `gsfonts-x11_0.17ubuntu4_all.deb'

100%[======================================>] 9,402       7.34K/s   in 1.3s    

2010-11-13 05:54:22 (7.34 KB/s) - `gsfonts-x11_0.17ubuntu4_all.deb' saved [9402/9402]

mike@mike-MacBook:~$ 
mike@mike-MacBook:~$                    sudo dpkg -i gsfont*.deb
[sudo] password for mike: 
Selecting previously deselected package gsfonts-x11.
(Reading database ... 118286 files and directories currently installed.)
Unpacking gsfonts-x11 (from gsfonts-x11_0.17ubuntu4_all.deb) ...
dpkg: dependency problems prevent configuration of gsfonts-x11:
 gsfonts-x11 depends on xutils (>= 4.1.0-12); however:
  Package xutils is not installed.
dpkg: error processing gsfonts-x11 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gsfonts-x11
mike@mike-MacBook:~$ 
I also tried using the instructions for synaptic on the ubuntu help and got

> mike@mike-MacBook:~$ sudo apt-get install ubuntu-restricted-extras
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package ubuntu-restricted-extras
mike@mike-MacBook:~$ 


Any ideas?


edit: it appears that this problem applies to more than just the restricted formats... I just tried to download chess and it didn't work either. the window flickered for a second after the "in progress" went away, then nothing happened.

---

### Post by dcstar on 2010-11-12
> **Onoku said:**
> 
..........
Any ideas?


edit: it appears that this problem applies to more than just the restricted formats... I just tried to download chess and it didn't work either. the window flickered for a second after the "in progress" went away, then nothing happened.

[LIST=1]
[*]Do not "quote" data.
[*]Go into Synaptic and select a new Repository.
[/LIST]

---

### Post by Onoku on 2010-11-12
Can someone give me a run down on how to enable the third party software repository?

---

### Post by jimmers on 2010-11-13
Go to Ubuntu Software Centre and look under EDIT


Luck

---

### Post by coffeecat on 2010-11-13
The package ubuntu-restricted-extras is in the Multiverse repository which should be enabled by default. In case it has been switched off, Ubuntu Software Centre > Edit > Software Sources > 'Ubuntu Software' tab. Make sure the 'Software restricted by copyright (multiverse)' box is ticked.

---

