---
title: "Backup ..."
date: 2010-09-26
forum: General Help
---

### Post by lulaz on 2010-09-26
Hello,

At first sorry for my english. I hope you will understand me.

I'm running two Ubuntu servers. One (remote) is my "work server", second is my home server. I would like to make daily backups of remote server on my home server. 
I read about rsync, but Im searching for some "ready to go" solutions (probably based on rsync, but scripted). I just want it to be simple - to specify destination machine, include and exclude directories (it would be nice if it would also support include/exclude for file types, file sizes). 
Support for hourly/daily/weekly snapshots is not mandatory - just a backup from last run. 
No GUI - just command line. 
Only changes in filesystem should be send to backup server (home server), so it would not send files already backed up.
Also, it would be great if it would build directory tree on the backup server. For example: if I want to make backup of /home/someuser and /usr/local/somedir then I would like to have this backed up at /main/backup/dir/home/someuser and /main/backup/dir/usr/local/somedir.

Please help :).

---

### Post by btindie on 2010-09-26
Take a look at these
 
[http://backuppc.sourceforge.net/](http://backuppc.sourceforge.net/)
[http://www.bacula.org/](http://www.bacula.org/)
[http://www.mikerubel.org/computers/rsync_snapshots/](http://www.mikerubel.org/computers/rsync_snapshots/)
[http://www.rsync.net/resources/howto/rsync_snapshots.html](http://www.rsync.net/resources/howto/rsync_snapshots.html)
[http://rsnapshot.org/](http://rsnapshot.org/)
[http://rdiff-backup.nongnu.org/](http://rdiff-backup.nongnu.org/)
[http://www.cis.upenn.edu/~bcpierce/unison/](http://www.cis.upenn.edu/~bcpierce/unison/)
 
 
If you're happy with rsync why don't you just write your own backup script that uses rsync?

---

### Post by kyphi on 2010-09-26
Your English is fine but your question makes little sense to me. What is a "ready to go" solution?

rsync is the program that will do all the things you require.  Read the documentation:

[http://www.samba.org/rsync/documentation.html](http://www.samba.org/rsync/documentation.html)

Even though you state that you prefer command line please consider Grsync which is a graphical front end to rsync.  It is in Synaptic.

---

