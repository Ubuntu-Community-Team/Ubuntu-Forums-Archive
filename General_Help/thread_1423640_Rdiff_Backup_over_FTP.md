---
title: "Rdiff Backup over FTP"
date: 2010-03-06
forum: General Help
---

### Post by Jason Cook on 2010-03-06
I have curlsftps installed and have mountered the FTP share to ~/STORAGE. When I run ```
rdiff-backup -b --exclude --exclude-symbolic-links --print-statistics --include /home/jason/ --include /etc/apt /home/jason /home/jason/STORAGE/Jason/Backup
```
I get this is the output.
```
Found interrupted initial backup. Removing...
Warning: hard linking not supported by filesystem at /home/jason/STORAGE/Jason/Backup/rdiff-backup-data
Exception 'Unable to open logfile /home/jason/STORAGE/Jason/Backup/rdiff-backup-data/backup.log: [Errno 95] Operation not supported: '/home/jason/STORAGE/Jason/Backup/rdiff-backup-data/backup.log'' raised of class '<class 'rdiff_backup.log.LoggerError'>':
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 304, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 324, in Main
    take_action(rps)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 280, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 337, in Backup
    backup_final_init(rpout)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 500, in backup_final_init
    Log.open_logfile(Globals.rbdir.append("backup.log"))
  File "/usr/lib/pymodules/python2.6/rdiff_backup/log.py", line 61, in open_logfile
    rpath.conn.log.Log.open_logfile_local(rpath)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/log.py", line 76, in open_logfile_local
    % (rpath.path, e))

Traceback (most recent call last):
  File "/usr/bin/rdiff-backup", line 30, in <module>
    rdiff_backup.Main.error_check_Main(sys.argv[1:])
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 304, in error_check_Main
    try: Main(arglist)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 324, in Main
    take_action(rps)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 280, in take_action
    elif action == "backup": Backup(rps[0], rps[1])
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 337, in Backup
    backup_final_init(rpout)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/Main.py", line 500, in backup_final_init
    Log.open_logfile(Globals.rbdir.append("backup.log"))
  File "/usr/lib/pymodules/python2.6/rdiff_backup/log.py", line 61, in open_logfile
    rpath.conn.log.Log.open_logfile_local(rpath)
  File "/usr/lib/pymodules/python2.6/rdiff_backup/log.py", line 76, in open_logfile_local
    % (rpath.path, e))
rdiff_backup.log.LoggerError: Unable to open logfile /home/jason/STORAGE/Jason/Backup/rdiff-backup-data/backup.log: [Errno 95] Operation not supported: '/home/jason/STORAGE/Jason/Backup/rdiff-backup-data/backup.log'

```
What am I doing wrong?

---

### Post by dcstar on 2010-03-06
> **Jason Cook said:**
> I have curlsftps installed and have mountered the **FTP share** to ~/STORAGE.
.........
What am I doing wrong?

FTP is a protocol that **only copies** files from one system to another, it is not a proper file sharing/access protocol like many others are.

---

### Post by Jason Cook on 2010-03-09
> **dcstar said:**
> FTP is a protocol that **only copies** files from one system to another, it is not a proper file sharing/access protocol like many others are.
 
If I can't do it over FTP would it work to do it over SAMBA?

---

