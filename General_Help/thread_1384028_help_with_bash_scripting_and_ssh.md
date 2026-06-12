---
title: "help with bash scripting and ssh"
date: 2010-01-17
forum: General Help
---

### Post by kylegio on 2010-01-17
i have a shell script on one computer which accesses another via ssh and tar's certain directories, it then gets the tar file (using "scp"), deletes the tar file from the remote computer, un-tar's the file on the local computer. it runs every hour or so as a backup method. 

first is there a better way to do this, or is this the best/easiest way to go about it?

second, the backup computer is not required to input a password to access the remote computer, however the process of connecting takes approximatly 30 seconds. this wastes a LOT of time because what im doing is
*connect -> tell computer to tar directories -> disconnect
*connect -> copy tar file to local  -> disconnect
untar file, check that it untarred properly
*connect -> delete remote file 

thats 3 connections, now i know how to do "tunneling" with ssh and how to put a connection to the background, is there a way i can connect once issue the commands i need to on the remote computer, then do the commands i need to on the local computer then go back to issuing commands on the remote computer, without the need to disconnect? 

my thoughts were i could do something like
ssh -f -L10110:localhost:22 remotemachine sleep 50

then somehow access that port every time i want to issue a command on the remote machine?

thoughts on how i can do this?

thanks

---

### Post by falconindy on 2010-01-17
If you need regular access to the filesystem (but not necessarily the CPU resources), why not just mount remote drive with sshfs?

---

### Post by john newbuntu on 2010-01-17
Just throwing this idea out: rsync over ssh or sbackup

---

