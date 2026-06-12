---
title: "Help with FTP or other fileshare"
date: 2011-10-21
forum: General Help
---

### Post by Weidbrewer on 2011-10-21
Hello, all.

Here's my situation:  I have some files that I would like to share with some friends that are too large to email.  I have my own domain that I use for a few other things, and I figured that it'd be great to just use that to transfer the files.  I thought that FTP would be my answer, but I rather naively jumped into it before I realized that I have *no* idea what I'm doing.

I looked through a number of vsftpd how-tos on the boards here, and *thought* I got it set up correctly, but now I don't know how to use it.  When I test it from the commandline (ftp 127.0.0.1) I seem to be able to log in, which is great - but I can't figure out how to actually do anything with it.  Also, using the Filezilla client on another computer, I can't seem to connect to it graphically.

For this, I filled the fields at the top:  My external IP, my name and password and my port.  It says it connects, but then times out.  (Also, I *thought* I'd set it to anonymous login, so shouldn't need the name and password...but maybe I misunderstood that.

Problem is, ever tutorial I've read seems to be geared towards sharing on a local network.

Bottom line, here's what I want to do:
[LIST=1]
[*]Have files in my /ftp folder
[*]Have other people be able to connect from outside my network
[*]Be able to link the IP of my FTP to myftp.mydomain.com  (Once I know how to actually use this FTP-thing, I know how to forward my IP to the address - just need to know the stuff leading up to this end-point.)
[/LIST]


my vsftp.conf was edited only for:

```
# Allow anonymous FTP? (Disabled by default)
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
#write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
local_umask=21
#I used 21, because that's the FTP port my router defaults to
```
I'm sure that this has been covered somewhere before - I've just been searching all night and can't find what I need.  If there's a how-to that you know of, please just point me in the right direction.

---

### Post by Weidbrewer on 2011-10-21
Also, here's the error I'm getting in Filezilla:

```

Status:	Connecting to <my IP>...
Status:	Connection established, waiting for welcome message...
Response:	220 Welcome to FTP service.
Command:	USER <my user name>
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
Response:	257 "/"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (<what looks like my local IP here>).
Status:	Server sent passive reply with unroutable address. Using server address instead.
Command:	LIST
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

---

