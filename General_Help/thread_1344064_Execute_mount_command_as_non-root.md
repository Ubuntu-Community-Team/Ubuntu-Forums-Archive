---
title: "Execute mount command as non-root"
date: 2009-12-02
forum: General Help
---

### Post by KennethRaugstad on 2009-12-02
Hi,

Is it possible to execute the mount command without using "sudo"? 

I have an Apple Mac Mini G4 that i use as an HTPC. This computer plays videos and music that i have stored on a fileserver and it uses NFS to access the files.

I have an ATI Remote Wonder remote control that works great with Ubuntu, my only problem is that i need to type in root password when i run my "connect to nfs server" shell script. 

I guess i could use the fstab file to mount the server when the computer boots up, but i would rather have the choice, and mount when i need to access the files. 

What i would like is to click the "Connect to server" icon that runs "gksudo /path/to/script" without getting password prompt. (Can´t type password with remote control) Is this possible? 

Sorry for my bad english and typing errors :-)

---

### Post by imbjr on 2009-12-02
Read up on sudoers ([https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)).

You can allow only yourself the privilege of using "sudo mount" without a password. Note you still need to prefix mount with sudo, but no password will be asked for once you have looked into sudoers.

---

