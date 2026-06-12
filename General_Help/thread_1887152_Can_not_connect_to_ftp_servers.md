---
title: "Can not connect to ftp servers"
date: 2011-11-26
forum: General Help
---

### Post by Mick54 on 2011-11-26
I everyone,

I am experimenting ftp connection issues with Ubuntu 10.10.
I usually use FileZilla and it works with most ftp servers but today I need to connect to a specific one and it fails however it works with FileZilla on Mac OSX with the same network connection.

FileZilla prompt on Ubutu :
 
> Status:	Resolving address of ftp.XXXX.com
Status:	Connecting to xxxx:21...
Status:	Connection established, waiting for welcome message...
Response:	220-
Response:	220-Bienvenue, 
Response:	220-
Status:	Invalid character sequence received, disabling UTF-8. Select UTF-8 option in site manager to force UTF-8.
Response:	220-       On Vous Héberge ?
Response:	220-           
Response:	220-Vous êtes connecté sur web764.
Response:	220 
Command:	USER connecth
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
Response:	211 End
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PORT 82,226,105,150,150,115
Response:	200 PORT command successful. Consider using PASV.
Command:	LIST
Response:	425 Failed to establish connection.
Error:	Failed to retrieve directory listing

on OSX :
> Status:	Resolving address of ftp.XXXX.com
Status:	Connecting to XXXX:21...
Status:	Connection established, waiting for welcome message...
Response:	220-
Response:	220-Bienvenue, 
Response:	220-
Response:	220-       On Vous Héberge ?
Response:	220-           
Response:	220-Vous êtes connecté sur web737.
Response:	220 
Command:	USER connecth
Response:	331 Please specify the password.
Command:	PASS ********
Response:	230 Login successful.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/"
Status:	Directory listing successful
Response:	421 Timeout.
Error:	Connection closed by server
Status:	Resolving address of ftp.connecthings.com
Status:	Connecting to 213.186.33.201:21...
Status:	Connection established, waiting for welcome message...
Response:	220-
Response:	220-Bienvenue, 
Response:	220-
Response:	220-       On Vous Héberge ?
Response:	220-           
Response:	220-Vous êtes connecté sur web604.
Response:	220 
Command:	USER connecth
Response:	331 Please specify the password.
Command:	PASS ********
Response:	230 Login successful.
Status:	Connected
Status:	Retrieving directory listing...
Command:	CWD /
Response:	250 Directory successfully changed.
Command:	PWD
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (213,186,33,201,92,41)
Command:	LIST
Response:	150 Here comes the directory listing.
Response:	226 Directory send OK.
Status:	Directory listing successful


I have inspected FileZilla configuration on both Mac OSX and Ubuntu. When I launched a test on Ubuntu (inside the "edit -> network configuration wizard") I got :

> Checking for correct external IP address
IP 192.168.1.5 bjc-bgi-b-f
Response: 510 Mismatch. Your IP is XXX.XXX.XXX.XXX, ic-ccg-baf-bfa
Wrong external IP address
Connection closed

Then I manually change external IP (my ISP use fixed IP) under FTP -> active mode.

Now when I launch the test :
> Connecting to probe.filezilla-project.org
Response: 220 FZ router and firewall tester ready
USER FileZilla
Response: 331 Give any password.
PASS 3.5.0
Response: 230 logged on.
Checking for correct external IP address
IP 82.226.105.150 ic-ccg-baf-bfa
Response: 200 OK
PREP 37327
Response: 200 Using port 37327, data token 972761184
PORT 82,226,105,150,145,207
Response: 200 PORT command successful
LIST
Response: 150 opening data connection
Response: 503 Failure of data connection.
Server sent unexpected reply.
Connection closed

I also try with gFtp and I have the same "List" problem.

Any suggestions?

Cheers
--
Armel

---

