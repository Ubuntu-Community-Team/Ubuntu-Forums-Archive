---
title: "KFTPgrabber, tls/ssl, problem with transfering files"
date: 2010-11-01
forum: General Help
---

### Post by claudelo on 2010-11-01
Hi,

I'm using ubuntu 10.10. 
I want to transfer files to a ftp server which specifies :  
[LIST]
[*]FTP/Host Address: webspace.bol.ucla.edu
[*]Port: 21
[*]Protocol Type: FTP with TLS/SSL (AUTH TLS - Explicit)
[*]Data Connection Type: PASV
[/LIST]
I installed KFTPgrabber (it looked like the simplest tool for this, but if you think something else is better, I will try). 
I tried to configure the connection. I have not used the info about the data connection type. 
What I have filled in the general settings : 
IP adress : webspace.bol.ucla.edu
port : 21
username : my_user_name
password : my_password
protocol : ftp
What I have filled in the security settings : 
ssl negotiation type : auth tls
I have not touched other settings. 

I manage to connect to the ftp server. I see my directory there. 

But I do not manage to transfer files from my desktop to my directory on the remote ftp server. The file is in the queue, but never get to the remote directory. Also, I cannot create a new folder in the remote directory. 

In the terminal from which I launched KFTPgrabber, numerous messages print, for example : 
Object::connect: Parentheses expected, signal KAction::triggered
X Error: BadWindow (invalid Window parameter) 3
  Major opcode: 20 (X_GetProperty)

I do not understand what is wrong, and what I could do to be able to use the ftp.

Thanks

Claude.

---

