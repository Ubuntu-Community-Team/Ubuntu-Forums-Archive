---
title: "pureftpd problems"
date: 2011-05-02
forum: General Help
---

### Post by LuniTux on 2011-05-02
Hello,

I am trying to run a ftp server on an Ubuntu 9.10 server computer. I have installed and configured everything based on 

[http://www.howtoforge.com/virtual-hosting-with-pureftpd-mysql-on-ubuntu-8.10]("http://www.howtoforge.com/virtual-hosting-with-pureftpd-mysql-on-ubuntu-8.10")

I can signin through my website but when I try to upload, I get the following error:

```
**[COLOR="Navy"][SIZE="4"]An error has occured[/SIZE][/COLOR]**
Could not generate a temporary file.

_[COLOR="Blue"]Go back[/COLOR]_ or _[COLOR="#0000ff"]Go to the login page[/COLOR]_

_[COLOR="#0000ff"]Hide technical details[/COLOR]_

 The error occured in file **/var/www/ftp/includes/filesystem.inc.php** on line **1773**.
 function acceptFiles ([SIZE="1"]/var/www/ftp/modules/upload/upload.inc.php on line 248[/SIZE]) 
 argument 0: Array
 function net2ftp_module_printBody ([SIZE="1"]/var/www/ftp/main.inc.php on line 314[/SIZE]) 
 function net2ftp (/var/www/ftp/index.php on line 61) 
 argument 0: printBody
```

I then tried to access the server via filezilla,

```
Status:	Connecting to xxx.xxx.xxx.xxx:21...
Status:	Connection established, waiting for welcome message...
Response:	220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
Response:	220-You are user number 1 of 20 allowed.
Response:	220-Local time is now 13:35. Server port: 21.
Response:	220-This is a private system - No anonymous login
Response:	220-IPv6 connections are also welcome on this server.
Response:	220 You will be disconnected after 15 minutes of inactivity.
Command:	USER ****
Response:	331 User **** OK. Password required
Command:	PASS ****
Response:	230-User **** has group access to:  2001      
Response:	230 OK. Current restricted directory is /
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Extensions supported:
Response:	 EPRT
Response:	 IDLE
Response:	 MDTM
Response:	 SIZE
Response:	 REST STREAM
Response:	 MLST type*;size*;sizd*;modify*;UNIX.mode*;UNIX.uid*;UNIX.gid*;unique*;
Response:	 MLSD
Response:	 AUTH TLS
Response:	 PBSZ
Response:	 PROT
Response:	 UTF8
Response:	 TVFS
Response:	 ESTA
Response:	 PASV
Response:	 EPSV
Response:	 SPSV
Response:	211 End.
Command:	OPTS UTF8 ON
Response:	200 OK, UTF-8 enabled
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is your current location
Command:	TYPE I
Response:	200 TYPE is now 8-bit binary
Command:	PASV
Response:	227 Entering Passive Mode (12,34,56,78,17,191)
Command:	MLSD

[COLOR="Red"]Error:	Connection timed out
Error:	Failed to retrieve directory listing[/COLOR]
```

It appears to work correctly but I do not get a list of the files and folders on the server for the selected user.

I finally tried using the terminal:

In the terminal I was able to successfully upload the file:

```
$ ftp xxx.xxx.xxx.xxx
Connected to xxx.xxx.xxx.xxx.
220---------- Welcome to Pure-FTPd [privsep] [TLS] ----------
220-You are user number 1 of 20 allowed.
220-Local time is now 14:19. Server port: 21.
220-This is a private system - No anonymous login
220-IPv6 connections are also welcome on this server.
220 You will be disconnected after 15 minutes of inactivity.
Name (xxx.xxx.xxx.xxx:****): ****
331 User **** OK. Password required
Password:
230-User **** has group access to:  2001      
230 OK. Current restricted directory is /
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> cd "testarea"
250 OK. Current directory is /Agency Export Files
ftp> put fakefile.txt
local: fakefile.txt remote: fakefile.txt
200 PORT command successful
150 Connecting to port 53712
226-File successfully transferred
226 0.001 seconds (measured here), 6.44 Kbytes per second
5 bytes sent in 0.00 secs (195.3 kB/s)
ftp> exit
221-Goodbye. You uploaded 1 and downloaded 0 kbytes.
221 Logout.
```

I checked the folder permissions and everything is 777 and the user and group are correctly set.

When I restart the server I get:

```
Restarting ftp server: Running: /usr/sbin/pure-ftpd-mysql -l mysql:/etc/pure-ftpd/db/mysql.conf -A -u 1000 -c 20 -X -b -x -8 UTF-8 -O clf:/var/log/pure-ftpd/transfer.log -R -E -C 4 -S ,21 -P 12.34.56.78 -p 4500:4600 -B

```

Any Ideas?

Thanks,

---

### Post by LuniTux on 2011-05-06
YAY PROGRESS!!!

I added the ftp port to the ufw exception list and changed the temp folder permissions and now I can use pureftpd to access, upload, and download files.

---

### Post by LuniTux on 2011-05-06
The only problem I am having now is the Filezilla error. It seems that the **mlsd** command is being blocked by the firewall. I shutoff apparmor and ufw and tried to connect again but I got the same response. I then tried Active mode and found that I can sign in, view the folders, upload, and download. This works with apparmor and ufw disabled and enabled. 

The problem is, I need to be able to access the server in regardless of mode. I read about the PassivePortRange file but the other server I have allows both modes and appears to have the same settings. The only difference I can see is that the new server **(Ubuntu 9.10 Server)** has **pure-ftpd version 1.0.22-1** and the old server **(CentOS 5.4)** has **pure-ftpd version 1.0.21**.

Is there a way to disable mlsd?

Are there any other firewall settings I am missing?

Is mlsd used in the previous pure-ftpd version? When I connect to the old server (Centos 5.4) using filezilla, I noticed that I do not see mlsd in the connection information.

If any more information is needed please let me know. 

Thanks,

---

### Post by LuniTux on 2011-08-03
I have found that ```
mlsd
``` appears to be a filezilla problem and not pureftpd

---

### Post by sblandford on 2012-10-25
Check the contents of the file,  /etc/pure-ftpd/conf/ForcePassiveIP.

This causes a hang for me with at mlsd in passive mode when I changed the server external IP address without remembering to update this file.

Also,   /etc/pure-ftpd/conf/PassivePortRange needs to agree with the port range opened in UFW for passive connections.

---

### Post by Bucky Ball on 2012-10-25
[I][B]Thread Closed

Reason:[/B][/I] Necromancy

---

