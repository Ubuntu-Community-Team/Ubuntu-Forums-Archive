---
title: "Duplicity"
date: 2012-09-26
forum: General Help
---

### Post by creiss on 2012-09-26
Hey folks,

running 12.04.1 LTS here (up to date), duplicity 0.6.18. I am doing a daily backup of my local system. The Full backup works fine, the first incremental too, but further incrementals crash with this error:

(You can see the full argument list et all there).

```

Using archive dir: /home/myuser/.cache/duplicity/79738e63cd90f8ccfbe70d8f1d0322f6
Using backup name: 79738e63cd90f8ccfbe70d8f1d0322f6
Import of duplicity.backends.gdocsbackend Succeeded
Import of duplicity.backends.hsibackend Succeeded
Import of duplicity.backends.botobackend Succeeded
Import of duplicity.backends.sshbackend Succeeded
Import of duplicity.backends.rsyncbackend Succeeded
Import of duplicity.backends.ftpsbackend Succeeded
Import of duplicity.backends.imapbackend Succeeded
Import of duplicity.backends.tahoebackend Succeeded
Import of duplicity.backends.u1backend Succeeded
Import of duplicity.backends.cloudfilesbackend Succeeded
Import of duplicity.backends.ftpbackend Succeeded
Import of duplicity.backends.localbackend Succeeded
Import of duplicity.backends.giobackend Succeeded
Import of duplicity.backends.webdavbackend Succeeded
Main action: full
================================================================================
duplicity 0.6.18 (February 29, 2012)
Args: /usr/bin/duplicity full --volsize 4096 --asynchronous-upload --encrypt-key 2A8FCC0B --encrypt-sign-key 2A8FCC0B --exclude /home/myuser/.wine --exclude /home/myuser/.Private --exclude /home/myuser/.gvfs --exclude /home/myuser/Videos --exclude /home/myuser/Storage --exclude /home/myuser/VirtualBox VMs --exclude /home/myuser/Pictures --exclude /home/myuser/.cache/duplicity/ --exclude /home/myuser/Music --exclude-other-filesystems --use-scp --verbosity 8 /home/myuser/ rsync://myuser@server1.remotebackup.com//home/myuser/backup/duplicity
Linux myclient 3.2.0-31-generic #50-Ubuntu SMP Fri Sep 7 16:16:45 UTC 2012 x86_64 x86_64
/usr/bin/python 2.7.3 (default, Aug  1 2012, 05:14:39) 
[GCC 4.6.3]
================================================================================
Using temporary directory /tmp/duplicity-wutNAP-tempdir
Temp has 72425639936 available, backup will use approx 9878424780.
Reading results of 'rsync -e 'ssh -oBatchMode=yes' myuser@server1.remotebackup.com:/home/myuser/backup/duplicity/'
Local and Remote metadata are synchronized, no sync needed.
Reading results of 'rsync -e 'ssh -oBatchMode=yes' myuser@server1.remotebackup.com:/home/myuser/backup/duplicity/'
Added incremental Backupset (start_time: Mon Sep 24 15:38:12 2012 / end_time: Tue Sep 25 13:00:03 2012)
Traceback (most recent call last):
  File "/usr/bin/duplicity", line 1403, in <module>
    with_tempdir(main)
  File "/usr/bin/duplicity", line 1396, in with_tempdir
    fn()
  File "/usr/bin/duplicity", line 1276, in main
    globals.archive_dir).set_values()
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 702, in set_values
    backup_chains)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 715, in set_matched_chain_pair
    sig_chains = sig_chains and self.get_sorted_chains(sig_chains)
  File "/usr/lib/python2.7/dist-packages/duplicity/collections.py", line 928, in get_sorted_chains
    assert len(chain_list) == 2
AssertionError

```

I tried using a giant search engine for help but to no avail. Any pointers would be aweseome.

---

### Post by mackstann on 2012-10-15
I would file a bug report with the project. They may also be able to find a fix or workaround for you in the meantime.

---

