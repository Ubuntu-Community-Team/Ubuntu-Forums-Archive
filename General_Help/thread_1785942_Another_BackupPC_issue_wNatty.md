---
title: "Another BackupPC issue w/Natty"
date: 2011-06-18
forum: General Help
---

### Post by z84976 on 2011-06-18
I just upgraded my wife's pc (which doubles as my BackupPC server... hehe) to 11.04. Everything seemed fine, but later I decided to add a new dev server VM to my BackupPC list to be backed up.  When done, I tried to initiate a full backup to get things started, but it didn't work.  I now realize *no* backups work since the upgrade (yesterday).  They all give the same error (I was backing up 3 machines + localhost) in the Log in the web gui:

2011-06-18 23:42:54 Failed to create directory 

Here are some relevant settings/etc on the backup server machine:

mount:
/dev/sdb on /backup type xfs (rw)  <--- (the big drive, with the stuff on it)

ls -la /var/lib
lrwxrwxrwx  1 root          root             7 2011-03-31 13:55 backuppc -> /backup   <--- (/var/lib/backuppc is a symlink to that /backup mount point)

root@thecomputer:/var/lib# ls -la /backup
total 8
drwxrwxrwx  8 backuppc backuppc   71 2011-03-31 13:54 .
drwxr-xr-x 24 root     root     4096 2011-06-17 23:57 ..
drwxr-x--- 18 backuppc backuppc  134 2011-06-18 20:25 cpool
drwxr-x---  2 backuppc backuppc 4096 2011-06-18 23:00 log
drwxr-x---  8 backuppc backuppc   93 2011-06-18 22:26 pc
drwxr-x---  2 backuppc backuppc    6 2010-08-12 05:46 pool
drwx------  2 backuppc backuppc  121 2011-06-18 22:02 .ssh
drwxr-x---  2 backuppc backuppc    6 2011-06-17 20:08 trash

in config.pl:
$Conf{Topdir} = '/backup';
$Conf{ConfDir} = '/etc/backuppc';
$Conf{LogDir} = '';
$Conf{InstallDir} = '/usr/share/backuppc';
$Conf{CgiDir} = '/usr/share/backuppc/cgi-bin';

It all worked REALLY well until the Natty upgrade.  Anybody seen similar?

(this is 32-bit ubuntu on amd64, if it matters)

---

### Post by upengan78 on 2011-12-13
I am in the same boat. Only difference is I am using Gentoo. Recent upgraded broke my backup jobs. Did you find solution to your issue? Please let me know. Thanks!

---

