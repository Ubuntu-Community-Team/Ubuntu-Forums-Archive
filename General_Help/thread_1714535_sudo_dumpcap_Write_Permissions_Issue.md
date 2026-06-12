---
title: "sudo dumpcap Write Permissions Issue"
date: 2011-03-25
forum: General Help
---

### Post by Conc on 2011-03-25
I ran into a permission error when trying to run dumpcap with the sudo   command.  I have since learned how to run dumpcap/wireshark/tshark   without root privileges ([http://ubuntuforums.org/showthread.php?t=1478198](http://ubuntuforums.org/showthread.php?t=1478198)),   but I am still perplexed by the error I am getting and thus why I am   posting this.  I am trying to convert from Windows to  Ubuntu, so I am  out of my comfort zone still.

I am using Ubuntu v10.10 32-bit and this is a basic install with no NFS drives.

Below is the command I am having trouble with:
```
mike@mike-linux:~$sudo dumpcap -i 2 -f "ip" -b duration:5 -b files:5 -w /home/mike/
```This is the output I receive:
```
The file to which the capture would be saved ("/home/mike/") could   not be opened: No such file or directory.
```My question is why   can't root write to my home folder?  My understanding is root should   have access to any file or folder on the _local_ system.

These are the directory permissions:
```
mike@mike-linux:/home$ pwd
/home
mike@mike-linux:/home$ ls -al
total 12
drwxr-xr-x  3 root  root  4096 2011-03-25 10:01 .
drwxr-xr-x 22 root  root  4096 2011-03-25 08:12 ..
drwxr-xr-x 27 mike mike 4096 2011-03-25 11:09 mike
```Any help would be greatly appreciated!

---

### Post by Conc on 2011-03-25
Apparently this is a reported bug in Ubuntu already and was first reported back in 2009.  Hopefully someone will be able to get to the bottom of it.

[https://bugs.launchpad.net/ubuntu/+source/wireshark/+bug/389467?comments=all](https://bugs.launchpad.net/ubuntu/+source/wireshark/+bug/389467?comments=all)

-Concolor

---

