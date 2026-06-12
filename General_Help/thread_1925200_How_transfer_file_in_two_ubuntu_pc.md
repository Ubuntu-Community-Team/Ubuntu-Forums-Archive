---
title: "How transfer file in two ubuntu pc ?"
date: 2012-02-14
forum: General Help
---

### Post by prismctg on 2012-02-14
How to transfer file in two ubuntu 11.10 pc ,i have a adsl modem and these machines are connected under same network.

---

### Post by SlugSlug on 2012-02-14
if ssh is installed you can 

places > connect to > remote ssh server

---

### Post by raja.genupula on 2012-02-14
[http://ubuntuforums.org/showthread.php?t=1410749](http://ubuntuforums.org/showthread.php?t=1410749)

[http://vikashazrati.wordpress.com/2008/02/03/quicktip-transferring-files-between-two-ubuntu-systems/](http://vikashazrati.wordpress.com/2008/02/03/quicktip-transferring-files-between-two-ubuntu-systems/)

---

### Post by TheFu on 2012-02-14
There are many different ways to transfer files on a network.  At least 1 machine must be a "server" and the other machine(s) would be "clients".

If there are any firewalls or the machines aren't within the same LAN subnet, then you may need to open ports and redirect TCP sockets to internal hosts and ports.  Usually there are not firewalls within most small LAN environments.

As SlugSlug says, using ssh, sftp, scp (all the same service) is probably the best way.   I googled for "ssh howto" and found this: [http://inside.mines.edu/~gmurray/HowTo/sshNotes.html](http://inside.mines.edu/~gmurray/HowTo/sshNotes.html)  If you didn't know about ssh, you'd never know to search.  Ssh is extremely powerful, yet can be extremely secure so I run an ssh server on every single Linux/UNIX machine.   Then you just need a userid on each machine with which you can connect.

There are lots of other ways to share files between systems - ftp (yuck), http, cifs, nfs, sshfs, rsync, ...  but using ssh/sftp/scp is the best for new users.  I've been using Linux for a long time and I still use ssh constantly. Mastering ssh is critical for anyone learning Linux.

---

