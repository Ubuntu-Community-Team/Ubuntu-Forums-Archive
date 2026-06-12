---
title: "Is it possible to recover a deleted file?"
date: 2010-03-01
forum: General Help
---

### Post by karthick87 on 2010-03-01
Recently i have deleted a text file and i have cleared my Trash..Now badly i need that file., is it possible to recover it?is there any recovery programs??

---

### Post by aysiu on 2010-03-01
Yes, but you have to stop using your computer right now and boot into a live CD session:
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles](http://www.psychocats.net/ubuntucat/recoverdeletedfiles)

---

### Post by karthick87 on 2010-03-02
I have deleted a log file in **/var/log **before 4 days back..how to recover it?

---

### Post by rnerwein on 2010-03-02
hi
have a look in your backups - no just a joke.
if you haven't reboot your system and the process to whom to the file belongs is still running and haven't call close the file you can get the contens of the file back ( because if you delete a file ( via rm ) you ain't delete the contens of the file - you are only delete the inode entry in the directory).
here is a example how to do it. e.g. you deleted a file wich belongs to rsyslogd - may be the file /var/log/messages.
1. ps -ef | grep rsyslogd
2. cd /proc/PID_OF_RSYSLOGD/fd
3. ls -l
4. cat FILE_NR_OF_MESSAGES >/tmp/blablu
then you will have the contents of messages in the file /tmp/blablu
now send syslog SIGHUP to tell him to create a new message file.
works with every file you delete and wich is still open by a process 
much fun
ciao

---

