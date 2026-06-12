---
title: "Unable to connect to FTP server with FileZilla"
date: 2010-10-11
forum: General Help
---

### Post by SRabin on 2010-10-11
My server is running Ubuntu 10.04 LTS Server with vsftpd. I run a Windows XP SP3 box with Ubuntu 10.04 as a VM in VirtualBox. Earlier today, I was uploading files from the VM to the server no problem; I've been fiddling on the server to configure it to run my web service and now I'm unable to connect to the server from Ubuntu. However, the FileZilla on my Windows installation has no problems connecting!

Some possibly relevant info:
(Server): cat /etc/vsftpd.conf | grep -v "#"
listen=YES
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

pasv_enable=YES
pasv_min_port=11000
pasv_max_port=11010

(Server): iptables -vL
Chain INPUT (policy ACCEPT 305K packets, 225M bytes)
 pkts bytes target     prot opt in     out     source               destination 
   51  2188 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpts:11000:11010

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 226K packets, 40M bytes)
 pkts bytes target     prot opt in     out     source               destination 

(Desktop): iptables -vL
Chain INPUT (policy ACCEPT 305K packets, 225M bytes)
 pkts bytes target     prot opt in     out     source               destination 
   51  2188 ACCEPT     tcp  --  any    any     anywhere             anywhere            tcp dpts:11000:11010

Chain FORWARD (policy ACCEPT 0 packets, 0 bytes)
 pkts bytes target     prot opt in     out     source               destination 

Chain OUTPUT (policy ACCEPT 226K packets, 40M bytes)
 pkts bytes target     prot opt in     out     source               destination 

When connecting to the FTP server, I see this:

Status:	Resolving address of [redacted]
Status:	Connecting to [redacted]:21...
Status:	Connection established, waiting for welcome message...
Response:	220 (vsFTPd 2.2.2)
Command:	USER [redacted]
Response:	331 Please specify the password.
Command:	PASS ********
Response:	230 Login successful.
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	 UTF8
Response:	211 End
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/var/www"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (205,186,165,172,204,187)
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing

Note: there is a rather sizable delay between the LIST command and the 'connection timed out'.

As the problem seems to be some configuration issue on either the server that I've been mucking with or the desktop (both host and guest have not had any options changed), I figured the Ubuntu forums would be the most likely place to figure out what the issue is.

Thanks in advance for any help!
-S

---

