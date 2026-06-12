---
title: "unable to start pure-ftpd-mysql"
date: 2010-01-08
forum: General Help
---

### Post by josepcols on 2010-01-08
Hi:
I've installed pure-ftpd.mysql V1.0.22.1  on an Ubuntu 9.10 and I'm unable to start.
The comand I use to start is: 
$ sudo service pure-ftpd-mysql start
Starting ftp server: Running: /usr/sbin/pure-ftpd-mysql -l mysql:/etc/pure-ftpd/db/mysql.conf -l puredb:/etc/pure-ftpd/pureftpd.pdb -l pam -O stats:/var/log/pure-ftpd/pureftpdstats.log -E -z -u 2000 -U 000:000 -8 UTF-8 -j -o -S 192.168.1.103,21 -p 58000:59000 -4 -Y 1 -D -P xx.xx.xx.xx -B
.
After this, the process does nothing:
$ ps -fea | grep ftp
root     31838     1  0 01:04 ?        00:00:00 /usr/sbin/pure-ftpd-mysql -l mysql:/etc/pure-ftpd/db/mysql.conf -l puredb:/etc/pure-ftpd/pureftpd.pdb -l pam -O stats:/var/log/pure-ftpd/pureftpdstats.log -E -z -u 2000 -U 000:000 -8 UTF-8 -j -o -S 192.168.1.103 21 -p 58000:59000 -4 -Y 1 -D -P xx.xx.xx.xx -B -g /var/run/pure-ftpd/pure-ftpd.pid
.
Log file /var/log/pure-ftpd/pureftpdstats.log has nothing.
Port 21 is not in LISTEN status.
.
Any idea to follow up?
Thanks in advance

---

### Post by josepcols on 2010-01-09
The problem is solved.
I use the -o option: uploadscript or call to external process after every upload
But I forget edit the file** [COLOR=#000000][B]/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]default[COLOR=#000000]**/**[/COLOR]pure-ftpd-common[/B]
The file [COLOR=#000000]**/**[/COLOR]etc[COLOR=#000000]**/**[/COLOR]default[COLOR=#000000]**/**[/COLOR]pure-ftpd-common must look like:
[COLOR=#007800]STANDALONE_OR_INETD[/COLOR]=standalone
[COLOR=#007800]VIRTUALCHROOT[/COLOR]=[COLOR=#C20CB9]**false**[/COLOR]
[COLOR=#007800]UPLOADSCRIPT[/COLOR]=[COLOR=#000000]**/**[/COLOR]path[COLOR=#000000]**/**[/COLOR]to[COLOR=#000000]**/**[/COLOR]pure-ftpd[COLOR=#000000]**/**[/COLOR]uploadscript
[COLOR=#007800]UPLOADUID[/COLOR]=[COLOR=#000000]0[/COLOR]
[COLOR=#007800]UPLOADGID[/COLOR]=[COLOR=#000000]0

[FONT=Arial]and, of course, it is needed to create the file [/FONT][/COLOR][COLOR=#000000]**/**[/COLOR]path[COLOR=#000000]**/**[/COLOR]to[COLOR=#000000]**/**[/COLOR]pure-ftpd[COLOR=#000000]**/**[/COLOR]uploadscript [FONT=Arial]and give execute privileges to it.[/FONT][COLOR=#000000]
[/COLOR]

---

