---
title: "smbmount"
date: 2006-06-28
forum: General Help
---

### Post by metallcoholix on 2006-06-28
I want to mount a volume using smbmount, however I dont seem to find the correct way of introducing the windows machine address or path. My windows machine is under the network home and has the hostname metallcoholix, but when I type into terminal: smbmount //metallcoholix /home/user/windows it doesnt seem to work, a message saying this command is designed to be run from within /bin/mount by giving the option -t smbfs, either this or a message saying nomountshare appears.
When i try to enter /bin/mount it says the file doesnt exists, and by looking to the /bin directories, the mount word appears highlited in red.
I right-clicked my windows machine under network servers and the address that appears is smb://metallcoholix. Does anyone knows how can I mount this volume???

---

### Post by schilcha on 2006-06-28
You need to specify the name of the windows-share (e.g //metallcoholix/mydocs) in the mount-statement.

Try having a look at this page, which should give you some valuable hints.
[https://help.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html#windows-networking-clients]("https://help.ubuntu.com/ubuntu/serverguide/C/configuring-samba.html#windows-networking-clients")

btw. the red-highlighted mount-commant seems ok, since the sticky bit is set. I guess "ls" wants to make sure you don't miss that fact. 

Good luck!

---

