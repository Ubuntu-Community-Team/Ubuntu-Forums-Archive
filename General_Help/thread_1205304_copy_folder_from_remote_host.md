---
title: "copy folder from remote host"
date: 2009-07-05
forum: General Help
---

### Post by mmbathan on 2009-07-05
Hi guys ,
 
I connect to remote host using ssh and I have an access to that host 
I need to copy a folder from this remote host to my host.
 
I use Vmware in my host to connect the remote host.
 
how  can I copy this folder?
 
Regards,

---

### Post by Boondoklife on 2009-07-05
check out scp it might help

---

### Post by mmbathan on 2009-07-05
I tried it but what the IP address that I have to use because I use VMware

---

### Post by Johnny B on 2009-07-05
scp -r username@IP:~/Foldername ~/Desktop

---

### Post by blueridgedog on 2009-07-05
or sftp...similar concept.

---

### Post by XCan on 2009-07-06
If you prefer an intuitive GUI while using sftp I could recommend you to use an FTP program, for example, gFTP (in synaptic). Using gFTP all you need to do is to connect to the server using protocol 'SSH2' instead of the default 'FTP'. Once you're connected, it will feel like you're on any ftp server.

---

