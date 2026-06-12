---
title: "&quot;mount.nfs4: mount system call failed&quot; and how to disconnect from sftp?"
date: 2010-08-17
forum: General Help
---

### Post by princeofnam on 2010-08-17
I'm trying to automatically mount my laptop's music folder onto my PC.  I tried using NFS, but I met with shaky results.  

I followed the directions at
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)

but when I got to the step

 mount -t nfs4 -o proto=tcp,port=2049 nfs-server:/export/users /home/users

I got

mount.nfs4: mount system call failed
--

so I gave up on that and tried to use ssh which worked but I don't know how to do two things
1) disconnect
2) connect automatically on startup

---

### Post by princeofnam on 2010-08-17
anyone? just a dude trying to listen to his tunes

---

### Post by princeofnam on 2010-08-18
bump :(

---

### Post by mythsmith on 2010-08-26
Hi, maybe it's not related to your problem, but for me the error appeared after an upgrade to 10.04. I checked all possible configurations, and all seemed fine. Then tried to ping the server, and found that it was not responding the machine I thought should (and which responded correctly before the upgrade).
So I checked my /etc/hosts configuration and found I wrote myserver address in a line like that:
 192.168.1.1  myserver, alias
Where both myserver and alias should be valid names for the machine.
I corrected it to:
 192.168.1.1  myserver alias
I know the old way of writing should never work, but always worked till 10.04 (starting from hardy).
After the correction, all is fine.

Another move you can try is going to the server and 
 dpkg-reconfigure portmap
Then select <NO> to the question you are asked.

Regards.

---

