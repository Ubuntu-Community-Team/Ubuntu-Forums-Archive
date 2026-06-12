---
title: "Cannot Upload Files with FTP to Guest OS"
date: 2010-12-08
forum: General Help
---

### Post by EliYui on 2010-12-08
I am running Ubuntu 10.10 server edition as a guest OS in Virtual Box.  I am trying to configure it as a web server to use for testing purposes for websites.  The present problem is that I cannot upload files to it using FTP.  I have installed the VSFTPD daemon on the server.  The server is connected to the Internet using the default NAT interface of Virtual Box.  I have run the following commands to configure port forwarding for FTP with Virtual Box:

```

VBoxManage modifyvm "Server Name" --natpf1 "FTP,tcp,,2020,,20"
VBoxManage modifyvm "Server Name" --natpf1 "FTP,tcp,,2121,,21"

```The host computer that I am using is a Macbook Pro (Intel) running 10.6.5.  I have tried the following FTP clients without success; Mac command line FTP, Filezilla, Classic FTP, Firefox 3.6.12.  I get the following errors with each of them:  

Mac command line FTP
```

$ ftp 127.0.0.1 [2121]
ftp: Unknown port `[2121]', using port 21
ftp: Can't connect to `127.0.0.1': Connection refused
ftp: Can't connect to `127.0.0.1'

```Filezilla
```

Status:    Connecting to 127.0.0.1:2121...
Status:    Connection established, waiting for welcome message...
Response:    220 (vsFTPd 2.3.0)
Command:    USER eliyui
Response:    331 Please specify the password.
Command:    PASS ********
Response:    230 Login successful.
Command:    SYST
Response:    215 UNIX Type: L8
Command:    FEAT
Response:    211-Features:
Response:     EPRT
Response:     EPSV
Response:     MDTM
Response:     PASV
Response:     REST STREAM
Response:     SIZE
Response:     TVFS
Response:     UTF8
Response:    211 End
Command:    OPTS UTF8 ON
Response:    200 Always in UTF8 mode.
Status:    Connected
Status:    Retrieving directory listing...
Command:    PWD
Response:    257 "/home/eliyui"
Command:    TYPE I
Response:    200 Switching to Binary mode.
Command:    PASV
Response:    227 Entering Passive Mode (10,0,2,15,146,73).
Command:    LIST
Error:    Connection timed out
Error:    Failed to retrieve directory listing

```Classic FTP (after trying to setup a new site)
```

FTP Connection Test Results
Server:  "localhost:2121" is OK.  
Logon details are OK.  
Current directory is:  /home/eliyui
Contains:  [no files]
Passive Connection Falied!
see www.nch.com.au/kb/10047.html
Unable to upload to the server.  

```Firefox 3.6.12
```

ftp://eliyui@localhost:2121

Produces the following error:  
Alert  425 Failed to establish connection.

```The configuration file for VSFTPD is the following:  
```

listen=yes
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem

```I also receive the following error when I try to restart VSFTPD with the following command:  
```

$ sudo /etc/init.d/vsftpd restart
[sudo] password for eliyui: 
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service vsftpd restart

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the restart(8) utility, e.g. restart vsftpd
vsftpd start/running, process 1079

```Want to configure FTP to be able to move files to the server.  Any suggestions?

---

### Post by EliYui on 2010-12-08
So I worked on the problem tonight and here is what I have done so far.  I connected my computer to my router directly with an Ethernet cord and then I changed the network configuration of my virtual server to bridged interface.  I logged in to determine the IP address of the server and to determine that it was receiving a valid address from my router.  Then using Filezilla was successfully able to transfer the files I needed to into my home directory.  

I was also able to access my server using FTP using Firefox, Mac command line FTP, and Classic FTP.

---

