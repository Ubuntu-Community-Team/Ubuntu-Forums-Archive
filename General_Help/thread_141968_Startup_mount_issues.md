---
title: "Startup mount issues"
date: 2006-03-09
forum: General Help
---

### Post by 1oki on 2006-03-09
hello all! I got a quick question for you. I was able to do this before and now even after reformating it still wont work. I have a network smb share that I want to mount on startup. I edited the fstab to look like this:

//192.168.1.90/backup         /media/backup smbfs credentials=/etc/fstab-cred,dmask=777,fmask=777   0      0


The fstab-cred file contains the approriate user name and password.
The mount point /media/backup is also legit. When I am in the system and use the command "mount -a" it returns this:
 mount -a
opts: rw
opts: credentials=/etc/fstab-cred
opts: dmask=777
opts: fmask=777
mount.smbfs started (version 3.0.14a-Ubuntu)
added interface ip=192.168.1.75 bcast=192.168.1.255 nmask=255.255.255.0
Connecting to 192.168.1.90 at port 445
error connecting to 192.168.1.90:445 (Connection refused)
Connecting to 192.168.1.90 at port 139


and it connects the share. All is well in my world... But when I reboot the system I get this:

connecting to 192.168.1.90 at port 445
error connecting to 192.168.1.90:445 (no route to host) 
connecting to 192.168.1.90 at port 139
error connecting to 192.168.1.90:139 (no route to host)
error connecting to 192.168.1.90 (no route to host)
5426: connection to 192.168.1.90 failed
SMB connection failed


 I used to be able to get a connection on port 139 on boot up... All is not well in my world... lol 

:-k any thoughts? thanks
-L

---

### Post by lamego on 2006-03-09
The file system is getting mounted before your network is properly setup...
To workaround this I would create an init script to do the mount after the network is setup.

---

### Post by 1oki on 2006-03-09
I would seem to be that wouldnt it... But the network comes up first. And in actuality this is one of the last steps taken in the boot process... Which is why I am boggled alittle... I thought it was because it was trying to mount it before the network comes up... 

Anyways, Im not good with scripting, so how would i do an init script? you dont have to walk me through it. Just point me in the right direction and I can find the info after that. thanks!

This is realy frustrating... :(

---

### Post by 1oki on 2006-03-13
Does anyone know what the Error code 5363 means? I get it when the network mount fails on bootup. I googled it, but could not find anything relevent on it. :confused:

---

### Post by 1oki on 2006-03-13
you guys can disregaurd this thread... I just added the mount -a command at the end of an init.d script and all seems to be working fine now! :)

Thanks lamego for getting me to think along these lines!

---

