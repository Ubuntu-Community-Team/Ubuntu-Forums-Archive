---
title: "Problems getting duplicity to work"
date: 2010-02-03
forum: General Help
---

### Post by signalsoldier74b on 2010-02-03
I have been trying to get duplicity to backup my files on my desktop to a server in the same physical location. Originally I tried scp, but could not get it to work. I recently tried file, but can't seem to get that working either.  I am running Ubuntu 8.10.

I have my remote server mounted using sshfs, and have no problems connecting. I can copy files to it, so I know it's not mounted read-only.

```

james@clay:~$ cp tmp.txt /media/myserver/Backups/James/tmp.txt
james@clay:~$ cd /media/myserver/Backups/James
james@clay:/media/myserver/Backups/James$ ls -l
total 8
-rw------- 1 root root 11 2010-02-03 23:46 tmp.txt

```However, when I try to use duplicity to backup my files to this location I receive an error.

```

james@clay:~$ mount /media/myserver
james@clay:~$ duplicity /home/james/Finances file:///media/myserver/Backups/James
No signatures found, switching to full backup.
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 482, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 477, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 468, in main
    full_backup(col_stats)
  File "/usr/bin/duplicity", line 172, in full_backup
    bytes_written = write_multivol("full", tarblock_iter, globals.backend)
  File "/usr/bin/duplicity", line 114, in write_multivol
    backend.put(tdp, dest_filename)
  File "/usr/lib/python2.5/site-packages/duplicity/backends.py", line 279, in put
    target_path.writefileobj(source_path.open("rb"))
  File "/usr/lib/python2.5/site-packages/duplicity/path.py", line 500, in writefileobj
    fout = self.open("wb")
  File "/usr/lib/python2.5/site-packages/duplicity/path.py", line 448, in open
    else: result = open(self.name, mode)
IOError: [Errno 74] Bad message: '/media/myserver/Backups/James/duplicity-full.2010-02-03T23:41:10-05:00.vol1.difftar.gpg'

```


I have tried different placement of the slashes (/), but nothing seems to work.  Please tell me what I'm doing wrong.  Thanks.

---

### Post by signalsoldier74b on 2010-02-06
Can anyone help?

---

