---
title: "sudo problem"
date: 2006-05-29
forum: General Help
---

### Post by saax on 2006-05-29
Hello

I install Ubunu 5.10 on Mac mini and almost everything works fine.
First i install xmms with command sudo apt-get install xmms and ask me to insert cd.Installation works fine,but now everytime i try to install something i got error like this

 ueulo@ubuntu:~$ su
Password:
su: Authentication failure
Sorry.

or 
root@ubuntu:~# sudo aptitude install irssi-text
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

Whats wrong ,please help me

---

### Post by johnc4510 on 2006-05-29
irssi and irssi-text come already install on dapper, and I assume on breezy too. So, there would be no packages to download and install. Also, you don't need to use su, only sudo for Ubuntu. Try another package install to see if it works or not.

---

### Post by saax on 2006-05-29
I try to install also VLC ,Fluxbox,BitchX,Azureus and always the same 

root@ubuntu:~# sudo aptitude install fluxbox
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Couldn't find any package whose name or description matched "fluxbox"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done

---

### Post by johnc4510 on 2006-05-29
Try this:
sudo apt-get install fluxbox
Let me know what happens

---

### Post by saax on 2006-05-29
root@ubuntu:~# sudo apt-get install fluxbox
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fluxbox

---

### Post by johnc4510 on 2006-05-29
Have you enabled the universe and multiverse repositories?

---

### Post by saax on 2006-05-29
Can u tell me how to enable this

---

### Post by johnc4510 on 2006-05-29
System>Administration>Synaptic Package Manager
Launch it and in the toolbar click settings then repositories
Put a check in all the boxes not checked and close the repositories window.
Click on reload, click on mark all updates, and click on apply
You may have some system updates to install, but after that you should be able to install anything in the synaptic window.

---

### Post by saax on 2006-05-29
Everything works fine now,

thank you very much johnc4510

---

