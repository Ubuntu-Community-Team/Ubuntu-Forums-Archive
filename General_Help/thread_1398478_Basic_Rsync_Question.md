---
title: "Basic Rsync Question"
date: 2010-02-04
forum: General Help
---

### Post by mcarrara on 2010-02-04
OK, I must be the densest person on the earth.  This should be simple and it is not working for me.  On a server (morgan) I am running rsync as a daemon using the command rsysnc --daemon.  On another server (crunch) I have files I want to copy to morgan.  I first see if I can connect by using the command rsync morgan: and I get a list of the directories in Root's home.  I can copy the files using the single colon (:).  I issue the command rsync morgan:: And it will not connect to the daemon.  Checking the logs on morgan I see nothing in the rsyncd log and in the syslog for daemons I see the crunch connected bu then it failed because the file /usr/sbin/rsyncd can't be found.  Of course it can't there is no such file.  the file is /usr/bin/sync.  I have a conffig file in /etc/rsyncd.conf.

What am I missing and why is rsync trying to connect to /usr/sbin/rsyncd?????

---

### Post by HermanAB on 2010-02-04
Howdy,

Nobody uses the rsync daemon, since it is it secure.  Rather use rsync over SSH (rsync -e ssh yadda yadda).  That always works for me without any issues.

---

