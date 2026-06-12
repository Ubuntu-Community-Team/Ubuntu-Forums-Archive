---
title: "SMB Share Error d???  - Works on 8.10 doesnt work on 9"
date: 2009-07-12
forum: General Help
---

### Post by rwmech on 2009-07-12
I am unable to mount SMB share across my network.  I am using 9.x with 2.6.28-11-generic kernel.

I have smbfs and smbclient installed.  

I have the correct mount information in my /etc/fstab and works PERFECTLY on my 8.10 SERVER however my workstation will not mount it properly with the same entry.

d????????? ? ?    ?       ?                ? storage

That is what shows up once the drive is mounted.  I know there is no problem with the mount command or fstab since this works fine on my server.  For some reason the workstation wont mount it properly.

Can anyone let me know what could be causing this?

---

### Post by rwmech on 2009-07-12
One thing I wanted to clarify, there are multiple systems involved here.  Both the server 8.10 and the workstation 9.04 are trying to connect to a NAS device running SMB as an embeded linux device. It's an AirNas101 but I don't think the NAS is the issue.  Something on the 9.04 workstation box is whack.

---

### Post by rwmech on 2009-07-13
Can anyone help out here? Does this post need to be moved to the networking forum?

---

### Post by rwmech on 2009-07-13
With some help from a friend we were able to figure out this problem.  While I still dont believe it myself the proof is in the pudding.

8.10 Version /etc/fstab entry
//192.168.0.101/storage/c /mnt/storage cifs gid=122,codepage=unicode,unicode 0 0

9.04 Version /etc/fstab entry
//192.168.0.101/storage /mnt/storage cifs gid=122,codepage=unicode,unicode 0 0


The only difference you'll notice there is the /c.  I'm presuming that there is something between the two version in 8.10 and 9.04 that cause the mapping difference.  smbclient behaved exactly the same way and ultimately was how we discovered the problem.

smbclient //192.168.0.101/storage 
worked while

smbclient //192.168.0.101/storage/c 
did not

What changed where in the 2 versions I dont know  but in any case I've got my network drive available again.

---

