---
title: "Creating Daemon Using update-rc.d, But Not Working After Reboot"
date: 2011-11-11
forum: General Help
---

### Post by robson9776 on 2011-11-11
Hi,

I have Ubuntu Desktop 11.10 installed on my PC and I created a file named 'mygammu' on /etc/init.d folder.

this 'mygammu' file contains this following lines :

#!/bin/sh
gammu-smsd -c /home/me/gammu01 --daemon
gammu-smsd -c /home/me/gammu02 --daemon
gammu-smsd -c /home/me/gammu03 --daemon

I also already change the permission into 755 to make it executable. then, I have a plan to execute this file everytime my PC is turned on by making it as a daemon using this command :

$ cd /etc/init.d/
$ sudo update-rc.d mygammu defaults

then, when I reboot my PC and I checked using this command :

$ ps aux | grep gammu

I found none of my gammu-smsd command running on the background. then I tried to re-install my daemon by removing it first using this command : 

$ sudo update-rc.d mygammu remove

I got this error message :

perl: warning: Setting locale failed.
perl: warning: Please check that your locale settings:
	LANGUAGE = (unset),
	LC_ALL = (unset),
	LC_CTYPE = "UTF-8",
	LANG = "en_US.UTF-8"
    are supported and installed on your system.
perl: warning: Falling back to the standard locale ("C").
update-rc.d: /etc/init.d/mygammu exists during rc.d purge (use -f to force)

is there something missing on what I've done? please advice... thanks.

---

### Post by dcstar on 2011-11-11
> **robson9776 said:**
> Hi,

I have Ubuntu Desktop 11.10 installed on my PC and I created a file named 'mygammu' on /etc/init.d folder.

this 'mygammu' file contains this following lines :

#!/bin/sh
gammu-smsd -c /home/me/gammu01 --daemon
gammu-smsd -c /home/me/gammu02 --daemon
gammu-smsd -c /home/me/gammu03 --daemon

I also already change the permission into 755 to make it executable. then, I have a plan to execute this file everytime my PC is turned on by making it as a daemon using this command :
........

Don't. Put the file somewhere else and the command in /etc/rc.local where it is supposed to be.

All files in those init folders are a specific format.

---

### Post by robson9776 on 2011-11-12
> **dcstar said:**
> Don't. Put the file somewhere else and the command in /etc/rc.local where it is supposed to be.

All files in those init folders are a specific format.

bro, you mean I have to put it 'mygammu' file in /home/me/ ? and what about /etc/rc.local? what should I do with it? should I put 'mygammu' file also there...

then when should I run this command in order to make it as a daemon : 
$ sudo update-rc.d mygammu defaults

I really frustrated with this, bro... please give me a clue... thanks :KS

---

