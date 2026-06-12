---
title: "installing problems with the software center"
date: 2009-12-05
forum: General Help
---

### Post by smile-its-smiley on 2009-12-05
Every time i try to install somthing i get the folowing message: 

Check if you are using third party repositories. If so disable them, since they are a common source of problems.
Furthermore run the following command in a Terminal: apt-get install -f

when i go in terminal 

sam@desktop:~$ apt-get install -f
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
sam@desktop:~$ 

Help please.

---

### Post by fluffman86 on 2009-12-05
sudo apt-get -f install

You have to add "sudo" before you can run system wide changes.  When it asks for your password, type it blindly: you won't see any stars echoed back to you.

---

### Post by smile-its-smiley on 2009-12-05
heres my results, but my printer has stopped working

sam@desktop:~$ sudo apt-get -f install
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies...Done
The following packages will be REMOVED
  pstocanonbj
0 upgraded, 0 newly installed, 1 to remove and 138 not upgraded.
1 not fully installed or removed.
After this operation, 250kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 128426 files and directories currently installed.)
Removing pstocanonbj ...
invoke-rc.d: unknown initscript, /etc/init.d/cupsys not found.
sam@desktop:~$

---

### Post by smile-its-smiley on 2009-12-05
I sorted the printer out, but i cant install anything again. But when i do sudo apt-get -f install, it makes my printer stop working then i can install but to use my printer i have to reinstall the drivers

My printer in a canon pixma ip1500

---

### Post by mickie.kext on 2009-12-05
Try to change server in "software sources". It is in system menu.

---

### Post by smile-its-smiley on 2009-12-05
How do i do that?

thanks

---

### Post by mickie.kext on 2009-12-05
> **smile-its-smiley said:**
> How do i do that?

thanks

You go to System --> Administration --> Software Sources. It is on top panel. Then chose some other server because that might be b0rked. It might be System --> Preferences --> Software Sources, I am on KDE right now so can't look. It should be easy to find:).

---

### Post by smile-its-smiley on 2009-12-05
Ive done that, but i still cant install anything without making my printer stopping.

---

