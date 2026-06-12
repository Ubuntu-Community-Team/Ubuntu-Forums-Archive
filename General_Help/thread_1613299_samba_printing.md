---
title: "samba printing"
date: 2010-11-04
forum: General Help
---

### Post by meandi2 on 2010-11-04
samba works, i can print from other computers great! (took me about 6h, on windows this would be a simple share click)

the catch:
after a reboot I need to do this:

sudo dpkg-reconfigure samba
(not sudo /etc/init.d/samba restart)(it runs as a deamon or at least it should)

to stop and start both smbd and nmbd (so it uses my smb.conf I think)

Can anyone place some input on how to fix this or what the possible cause is?

Samba config:
> 
testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: rlimit_max (1024) below minimum Windows limit (16384)
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	workgroup = MSHOME
	security = SHARE
	printcap name = cups
	addprinter command = /usr/bin/addcupsprt
	guest only = Yes

[printers]
	comment = All Printers
	path = /var/spool/samba
	printable = Yes
	use client driver = Yes
	browseable = No
	browsable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers


log.smbd
> 
[2010/11/04 15:28:27,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/11/04 15:28:27,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/11/04 15:28:27,  0] printing/print_cups.c:103(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2010/11/04 15:28:27,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/11/04 15:28:28,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/11/04 15:28:28,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[B][2010/11/04 15:32:24,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/11/04 15:32:24,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option[/B]


log.nmbd
> 
[2010/11/04 15:28:31,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[B][2010/11/04 15:32:22,  0] nmbd/nmbd.c:71(terminate)
  Got SIGTERM: going down...
[2010/11/04 15:32:24,  0] nmbd/nmbd.c:854(main)
  nmbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009[/B]


---

### Post by meandi2 on 2010-11-04
possible solutions: (did not work for me)
[https://bbs.archlinux.org/viewtopic.php?id=70386]("https://bbs.archlinux.org/viewtopic.php?id=70386")
[http://www.linuxquestions.org/questions/linux-general-1/cups-unable-to-connect-to-server-184088/]("http://www.linuxquestions.org/questions/linux-general-1/cups-unable-to-connect-to-server-184088/")

---

### Post by Morbius1 on 2010-11-04
The real question is why are you printing through Samba.

Anyway, there is no /etc/init.d/samba anymore. It's now been replaced with it's component daemons: smbd and nmbd. To restart smbd itself:
```
sudo service smbd restart
```More than likely you are the victum of a bug where cups starts after smbd starts. Samba reads the printer list from cups during the service start or restart. If cups hasn't started yet there are no printers for samba to see.

To fix that:

Edit /etc/init/smbd.conf and change this:
> description "SMB/CIFS File Server"
author "Steve Langasek <steve.langasek@ubuntu.com>"

**[COLOR=Blue]start on local-filesystems[/COLOR]**
stop on runlevel [!2345]

respawn

pre-start script
RUN_MODE="daemons"

[ -r /etc/default/samba ] && . /etc/default/samba

[ "$RUN_MODE" = inetd ] && { stop; exit 0; }

install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -Fto this:
> description "SMB/CIFS File Server"
author "Steve Langasek <steve.langasek@ubuntu.com>"

[COLOR=Blue]**start on (local-filesystems and stopped rc)**[/COLOR]
stop on runlevel [!2345]

respawn

pre-start script
RUN_MODE="daemons"

[ -r /etc/default/samba ] && . /etc/default/samba

[ "$RUN_MODE" = inetd ] && { stop; exit 0; }

install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -F 

---

### Post by meandi2 on 2010-11-04
I did find solution and was returning to post it:

[https://bugs.launchpad.net/ubuntu/+source/cups/+bug/494141]("https://bugs.launchpad.net/ubuntu/+source/cups/+bug/494141")

> 
I have the same problem too. I solved it by adding

sleep 60
restart smbd

to /etc/rc.local.


...When I saw your response, thank you for that anyways :p. (Your solution seems to be better.)

And I print with samba cause when I boot this computer in windows 7 other computers can use the same location to print. (unless I don't need samba for that then I use samba cause I don't know any better :redface:)

---

