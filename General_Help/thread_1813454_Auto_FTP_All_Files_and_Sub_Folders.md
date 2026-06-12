---
title: "Auto FTP All Files and Sub Folders"
date: 2011-07-27
forum: General Help
---

### Post by techanalyst on 2011-07-27
Ive been trying to figure out a method to upload (copy) all files and sub folders under that folder to my content delivery network, basically run it every 30 minutes.

Whats the best way to do it?  I tested a few that I was reading about, one just copied files nd not sub folders, another moved all files.

---

### Post by galvatron408 on 2011-07-30
you should put in your crontab...

30 * * * * rsync /mydir user@remotehost:/someremotedir/.

this will copy all files plus the directory "mydir" to the remote host and place it in /someremotedir/

Best of all, since it is rsync, the next 30 minute goes by, you won't be uploading everything. Instead, you'll just be syncing the difference! nice huh?

---

### Post by galvatron408 on 2011-07-30
oh yea, i forgot. you're ganna need to setup ssh keys. :)

and... i forgot to say... add -av --progress if you want to use archive and verbose and see the copy progress but I suppose since you're going to cron it, you probably can omit --progress.

---

