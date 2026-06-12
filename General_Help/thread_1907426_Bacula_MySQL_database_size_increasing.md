---
title: "Bacula MySQL database size increasing"
date: 2012-01-11
forum: General Help
---

### Post by tezarin on 2012-01-11
Hi all,
I have been using Bacula to backup several servers. Recently, the backupcatalog job takes so long to finish. I'm pretty sure it's related to the size of bacula.sql file. 
```

ls root@servername:/var/lib/bacula# ls -l
-rw------- 1 bacula bacula 208285783 2012-01-10 05:23 bacula.sql

```
I've been reading bacula catalog manual here: [http://www.bacula.org/3.0.x-manuals/en/catalog/catalog.pdf](http://www.bacula.org/3.0.x-manuals/en/catalog/catalog.pdf)
and in the 1.2 Compacting Your MySQL Database section, it's talking about compacting the database:
I have been handed this server by the previous IT guy and don't have the info required to access the MySQL database.
This is the part of bacula-dir.conf which has the reference to the bacula.sql:
```

# This is the backup of the catalog
FileSet {
  Name = "Catalog"
  Include {
    Options {
      signature = MD5
    }
    File = "/var/lib/bacula/bacula.sql"
  }
}

```
 
Can someone please let me know how I can compact the bacula database?
Thanks,
t

---

### Post by Habitual on 2012-01-11
Terminal > 
```
du -sh /var/lib/mysql/bacula/
```

---

### Post by Habitual on 2012-01-11
..."You will then need to follow the instructions for your database type to recreate the database from the
ASCII backup file"

Optimizing:
mysqldump -f --opt bacula > bacula.sql
mysql -uroot -p bacula < /var/lib/bacula/bacula.sql

Bacula Bacula Main Reference
dated: November 7, 2011

Section 48.2
Page 374

---

### Post by tezarin on 2012-01-11
> **Habitual said:**
> Terminal > 
```
du -sh /var/lib/mysql/bacula/
```
 
Thanks for your reply.
Here's the output:
 
```

root@servername:/etc/init.d# du -sh /var/lib/mysql/bacula/
814M    /var/lib/mysql/bacula/

```
 
I just reset MySQL root password but can't really see user bacula's db password in bacula-dir.conf as it appears to be encrypted.
 
I just followed your advice and ran the following commands:
 
> 
mysqldump -f --opt bacula > bacula.sql
mysql bacula < bacula.sql
rm -f bacula.sql

 
But when I checked the size of the database it's still really large:
 
> 
root@servername:/var/lib# cd bacula
root@servername:/var/lib/bacula# ls -l
-rw------- 1 bacula bacula 208285783 2012-01-10 05:23 bacula.sql

 
Maybe I didn't do this correctly?
 
Edit - I just ran the size command again and looks like it's much smaller now:
> 
[EMAIL="root@servername:/var/lib"]root@servername:/var/lib[/EMAIL]# du -sh /var/lib/mysql/bacula/
299M    /var/lib/mysql/bacula/


 
Thanks for your help. Now the backup catalog job should be done faster as it's using the bacula.sql file. I'll report back.
 
Regards,
t

---

### Post by Habitual on 2012-01-11
glad it worked out.

---

### Post by tezarin on 2012-01-12
> **Habitual said:**
> glad it worked out.
 
The database appeared to be smaller but today the backupcatalog job failed:
 
```

12-Jan 05:39 babar-dir JobId 1639: shell command: run BeforeJob "/etc/bacula/scripts/make_catalog_backup.pl MyCatalog"
12-Jan 05:39 babar-dir JobId 1639: BeforeJob: sh: cannot create /var/lib/bacula/bacula.sql: Permission denied
12-Jan 05:39 babar-dir JobId 1639: Error: Runscript: BeforeJob returned non-zero status=2. ERR=Child exited with code 2
12-Jan 05:39 babar-dir JobId 1639: Error: Bacula babar-dir 5.0.1 (24Feb10): 12-Jan-2012 05:39:13
  Build OS:               x86_64-pc-linux-gnu ubuntu 10.04
  JobId:                  1639
  Job:                    BackupCatalog.2012-01-11_21.55.00_45
  Backup Level:           Full
  Client:                 "babar-fd" 5.0.1 (24Feb10) x86_64-pc-linux-gnu,ubuntu,10.04
  FileSet:                "Catalog" 2011-02-03 01:10:00
  Pool:                   "File" (From Job resource)
  Catalog:                "MyCatalog" (From Client resource)
  Storage:                "File" (From Job resource)
  Scheduled time:         11-Jan-2012 21:55:00
  Start time:             12-Jan-2012 05:39:13
  End time:               12-Jan-2012 05:39:13
  Elapsed time:           0 secs
  Priority:               11
  FD Files Written:       0
  SD Files Written:       0
  FD Bytes Written:       0 (0 B)
  SD Bytes Written:       0 (0 B)
  Rate:                   0.0 KB/s
  Software Compression:   None
  VSS:                    no
  Encryption:             no
  Accurate:               no
  Volume name(s):
  Volume Session Id:      0
  Volume Session Time:    0
  Last Volume Bytes:      0 (0 B)
  Non-fatal FD errors:    1
  SD Errors:              0
  FD termination status:
  SD termination status:
  Termination:            *** Backup Error ***

```
 
Since it's a permission error, I probably should run something like 
```
chown someuser:someuser /var/lib/bacula
```
 
But can't figure out if it should be bacula:bacula or root:bacula or mysql:bacula...
 
Would you help me figure this out please? Thank you

---

### Post by Habitual on 2012-01-12
I have root:bacula on mine so....
```
chown root:bacula /var/lib/bacula/bacula.sql
```

-rw-rw---- 1 root bacula 413K Jan 11 23:10 /var/lib/bacula/bacula.sql

---

### Post by tezarin on 2012-01-12
> **Habitual said:**
> I have root:bacula on mine so....
```
chown root:bacula /var/lib/bacula/bacula.sql
```
 
-rw-rw---- 1 root bacula 413K Jan 11 23:10 /var/lib/bacula/bacula.sql
 
Thanks, I made that change and tried to run a test job (backupcatalog), it failed again with the same error as before:
 
```

12-Jan 14:13 babar-dir JobId 1645: shell command: run BeforeJob "/etc/bacula/scripts/make_catalog_backup.pl MyCatalog"
12-Jan 14:13 babar-dir JobId 1645: BeforeJob: sh: cannot create /var/lib/bacula/bacula.sql: Permission denied
12-Jan 14:13 babar-dir JobId 1645: Error: Runscript: BeforeJob returned non-zero status=2. ERR=Child exited with code 2
12-Jan 14:13 babar-dir JobId 1645: Error: Bacula babar-dir 5.0.1 (24Feb10): 12-Jan-2012 14:13:41
  Build OS:               x86_64-pc-linux-gnu ubuntu 10.04
  JobId:                  1645
  Job:                    BackupCatalog.2012-01-12_14.13.39_04
  Backup Level:           Full
  Client:                 "babar-fd" 5.0.1 (24Feb10) x86_64-pc-linux-gnu,ubuntu,10.04
  FileSet:                "Catalog" 2011-02-03 01:10:00
  Pool:                   "File" (From Job resource)
  Catalog:                "MyCatalog" (From Client resource)
  Storage:                "File" (From Job resource)
  Scheduled time:         12-Jan-2012 14:13:38
  Start time:             12-Jan-2012 14:13:41
  End time:               12-Jan-2012 14:13:41
  Elapsed time:           0 secs
  Priority:               11
  FD Files Written:       0
  SD Files Written:       0
  FD Bytes Written:       0 (0 B)
  SD Bytes Written:       0 (0 B)
  Rate:                   0.0 KB/s
  Software Compression:   None
  VSS:                    no
  Encryption:             no
  Accurate:               no
  Volume name(s):
  Volume Session Id:      0
  Volume Session Time:    0
  Last Volume Bytes:      0 (0 B)
  Non-fatal FD errors:    1
  SD Errors:              0
  FD termination status:
  SD termination status:
  Termination:            *** Backup Error ***
 
 
I noticed the write permission is not granted: -rw-r--r-- 1 root   bacula 209927918 2012-01-12 13:45 bacula.sql
 

```
 
Also got a new error saying:
 
```
Fatal error: bsock.c:135 Unable to connect to Client: gauss-fd on gauss:9102. ERR=Connection refused
``` 
 
Gauss is the name of my mail server.
 
```

 
root@servername:/var/lib/bacula# cd /etc/bacula/scripts
root@servername:/etc/bacula/scripts# ls -l
total 72
-rw-r--r-- 1 root root 296 2010-03-23 16:27 btraceback.gdb
-rwxr-xr-x 1 root root 112 2010-03-23 16:27 delete_catalog_backup
-rwxr-xr-x 1 root root 9012 2010-03-23 16:27 disk-changer
-rwxr-xr-x 1 root root 16948 2010-03-23 16:27 dvd-handler
-rwxr-xr-x 1 root root 2047 2010-03-23 16:27 make_catalog_backup
-rw-r--r-- 1 root root 1646 2010-03-23 16:27 make_catalog_backup_awk
-rwxr-xr-x 1 root root 4106 2010-03-23 16:27 make_catalog_backup.pl
-rwxr-xr-x 1 root root 6899 2010-03-23 16:27 mtx-changer
-rwxr-xr-x 1 root root 1506 2010-03-23 16:27 mtx-changer.conf
-rw-r--r-- 1 root root 90 2010-03-23 16:27 query.sql
 
 

```

---

### Post by Habitual on 2012-01-12
> **tezarin said:**
> Thanks, I made that change and tried to run a test job 
did you restart all bacula services or run bconsole > reload after this edit?

---

### Post by tezarin on 2012-01-13
Good point, I reload it right now, thank you very much.
 
Here's the error log. I got this error after running the backupcatalog job:
```


13-Jan 14:51 babar-dir JobId 1651: shell command: run BeforeJob "/etc/bacula/scripts/make_catalog_backup.pl MyCatalog"
13-Jan 14:51 babar-dir JobId 1651: BeforeJob: sh: cannot create /var/lib/bacula/bacula.sql: Permission denied
13-Jan 14:51 babar-dir JobId 1651: Error: Runscript: BeforeJob returned non-zero status=2. ERR=Child exited with code 2
13-Jan 14:51 babar-dir JobId 1651: Error: Bacula babar-dir 5.0.1 (24Feb10): 13-Jan-2012 14:51:00
  Build OS:               x86_64-pc-linux-gnu ubuntu 10.04
  JobId:                  1651
  Job:                    BackupCatalog.2012-01-13_14.50.58_30
  Backup Level:           Full
  Client:                 "babar-fd" 5.0.1 (24Feb10) x86_64-pc-linux-gnu,ubuntu,10.04
  FileSet:                "Catalog" 2011-02-03 01:10:00
  Pool:                   "File" (From Job resource)
  Catalog:                "MyCatalog" (From Client resource)
  Storage:                "File" (From Job resource)
  Scheduled time:         13-Jan-2012 14:50:56
  Start time:             13-Jan-2012 14:51:00
  End time:               13-Jan-2012 14:51:00
  Elapsed time:           0 secs
  Priority:               11
  FD Files Written:       0
  SD Files Written:       0
  FD Bytes Written:       0 (0 B)
  SD Bytes Written:       0 (0 B)
  Rate:                   0.0 KB/s
  Software Compression:   None
  VSS:                    no
  Encryption:             no
  Accurate:               no
  Volume name(s):
  Volume Session Id:      0
  Volume Session Time:    0
  Last Volume Bytes:      0 (0 B)
  Non-fatal FD errors:    1
  SD Errors:              0
  FD termination status:
  SD termination status:
  Termination:            *** Backup Error ***

```
 
I've noticed my Zimbra mail server will be accessible at 7:15-ish every morning (at best sometimes it takes until 8:15 to start working). It goes down sometimes at night (due to bacula backup process) but the backup process ends around 5 AM so I am not sure why the mail server stays down for two three hours after the backup process ended. This is the log I found on the mail server, could you please help me with this problem?
Thanks in advance
 
```

Jan 13 07:15:18 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping Global system configuration update. 
Jan 13 07:15:18 mail zimbramon[31338]: 31338:info: zmmtaconfig: gacf ERROR: service.FAILURE (system failure: ZimbraLdapContext) (cause: javax.naming.CommunicationException gauss.domain.com:389)  
Jan 13 07:15:19 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping All Reverse Proxy URLs update. 
Jan 13 07:15:19 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping getAllReverseProxyURLs ERROR: service.FAILURE (system failure: ZimbraLdapContext) (cause: javax.naming.CommunicationException gauss.domain.com:389)  
Jan 13 07:15:19 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping All Reverse Proxy Backends update. 
Jan 13 07:15:19 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping getAllReverseProxyBackends ERROR: service.FAILURE (system failure: ZimbraLdapContext) (cause: javax.naming.CommunicationException gauss.domain.com:389)  
Jan 13 07:15:20 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping All Memcached Servers update. 
Jan 13 07:15:20 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping getAllMemcachedServers ERROR: service.FAILURE (system failure: ZimbraLdapContext) (cause: javax.naming.CommunicationException gauss.domain.com:389)  
Jan 13 07:15:21 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping All MTA Authentication Target URLs update. 
Jan 13 07:15:21 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping getAllMtaAuthURLs ERROR: service.FAILURE (system failure: ZimbraLdapContext) (cause: javax.naming.CommunicationException gauss.domain.com:389)  
Jan 13 07:15:21 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping Configuration for server gauss.domain.com update. 
Jan 13 07:15:21 mail zimbramon[31338]: 31338:info: zmmtaconfig: gs:gauss.domain.com ERROR: service.FAILURE (system failure: ZimbraLdapContext) (cause: javax.naming.CommunicationException gauss.domain.com:389)  
Jan 13 07:15:21 mail zimbramon[31338]: 31338:info: zmmtaconfig: Sleeping...Key lookup failed. 
Jan 13 07:15:26 mail zimbramon[6828]: 6828:info: Starting services initiated by zmcontrol 
Jan 13 07:15:27 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping Global system configuration update. 
Jan 13 07:15:27 mail zimbramon[31338]: 31338:info: zmmtaconfig: gacf ERROR: service.FAILURE (system failure: ZimbraLdapContext) (cause: javax.naming.CommunicationException gauss.domain.com:389)  
Jan 13 07:15:28 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping All Reverse Proxy URLs update. 
Jan 13 07:15:28 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping getAllReverseProxyURLs ERROR: service.FAILURE (system failure: ZimbraLdapContext) (cause: javax.naming.CommunicationException gauss.domain.com:389)  
Jan 13 07:15:28 mail slapd[7019]: @(#) $OpenLDAP: slapd 2.3.42 (May 29 2008 13:41:01) $  build@build11:/home/build/p4/main/ThirdParty/openldap/openldap-2.3.42.6z/servers/slapd 
Jan 13 07:15:28 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping All Reverse Proxy Backends update. 
Jan 13 07:15:28 mail zimbramon[31338]: 31338:info: zmmtaconfig: Skipping getAllReverseProxyBackends ERROR: service.FAILURE (system failure: ZimbraLdapContext) (cause: javax.naming.CommunicationException gauss.domain.com:389)  
Jan 13 07:15:29 mail slapd[7131]: slapd starting 
Jan 13 07:15:33 mail zimbramon[31338]: 31338:info: zmmtaconfig: Sleeping...Key lookup failed. 
Jan 13 07:15:35 mail zimbramon[6828]: 6828:info: Rewriting configs  antispam amavis antivirus amavis imapproxy   webxml mailbox amavis antispam antivirus mta sasl    
Jan 13 07:15:47 mail zimbramon[6828]: 6828:info: Starting logger via zmcontrol 
Jan 13 07:15:47 mail zimbramon[6828]: 6828:info: Starting mailbox via zmcontrol 
Jan 13 07:15:48 mail zimbramon[8086]: 8086:info: zmmtaconfig: zmmtaconfig already running at 31338 
Jan 13 07:16:09 mail zmmailboxdmgr[9041]: status requested
Jan 13 07:16:09 mail zmmailboxdmgr[9041]: file /opt/zimbra/log/zmmailboxd_manager.pid does not exist
Jan 13 07:16:09 mail zmmailboxdmgr[9041]: assuming no other instance is running
Jan 13 07:16:09 mail zmmailboxdmgr[9041]: file /opt/zimbra/log/zmmailboxd.pid does not exist
Jan 13 07:16:09 mail zmmailboxdmgr[9041]: assuming no other instance is running
Jan 13 07:16:09 mail zmmailboxdmgr[9041]: no manager process is running
Jan 13 07:16:09 mail zmmailboxdmgr[9048]: start requested
Jan 13 07:16:09 mail zmmailboxdmgr[9048]: checking if another instance of manager is already running
Jan 13 07:16:09 mail zmmailboxdmgr[9048]: file /opt/zimbra/log/zmmailboxd_manager.pid does not exist
Jan 13 07:16:09 mail zmmailboxdmgr[9048]: assuming no other instance is running
Jan 13 07:16:09 mail zmmailboxdmgr[9048]: file /opt/zimbra/log/zmmailboxd.pid does not exist
Jan 13 07:16:09 mail zmmailboxdmgr[9048]: assuming no other instance is running
Jan 13 07:16:09 mail zimbramon[6828]: 6828:info: Starting imapproxy via zmcontrol 
Jan 13 07:16:09 mail zmmailboxdmgr[9049]: wrote manager pid 9049 to /opt/zimbra/log/zmmailboxd_manager.pid
Jan 13 07:16:09 mail zmmailboxdmgr[9049]: manager started mailboxd/JVM with pid 9052
Jan 13 07:16:09 mail zmmailboxdmgr[9052]: wrote java pid 9052 to /opt/zimbra/log/zmmailboxd_java.pid
Jan 13 07:16:10 mail zimbramon[6828]: 6828:info: Starting antispam via zmcontrol 
Jan 13 07:16:11 mail zimbramon[9106]: 9106:info: zmmtaconfig: zmmtaconfig already running at 31338 
Jan 13 07:16:13 mail amavis[9170]: starting.  /opt/zimbra/amavisd/sbin/amavisd at gauss.domain.com amavisd-new-2.5.4 (20080312), Unicode aware, LANG="en_US.UTF-8"
Jan 13 07:16:13 mail amavis[9170]: user=500, EUID: 500 (500);  group=, EGID: 500 501 500 5 4 (500 501 500 5 4)
Jan 13 07:16:13 mail amavis[9170]: Perl version               5.008008
Jan 13 07:16:16 mail amavis[9170]: SpamControl: init_pre_chroot done
Jan 13 07:16:16 mail amavis[9186]: Net::Server: Process Backgrounded
Jan 13 07:16:16 mail amavis[9186]: Net::Server: 2012/01/13-07:16:16 Amavis (type Net::Server::PreForkSimple) starting! pid(9186)
Jan 13 07:16:16 mail amavis[9186]: Net::Server: Binding to UNIX socket file /opt/zimbra/data/amavisd/amavisd.sock using SOCK_STREAM
Jan 13 07:16:16 mail zimbramon[6828]: 6828:info: Starting antivirus via zmcontrol 
Jan 13 07:16:16 mail amavis[9186]: Net::Server: Binding to TCP port 10024 on host 127.0.0.1

```

---

### Post by Habitual on 2012-01-13
I don't mess with no zimbra, sorry.
I'd check something in addition to the bacula job summary you provided.

Perhaps the mailing list could help.
They are very active and responsive.

[http://www.bacula.org/en/?page=maillists](http://www.bacula.org/en/?page=maillists)

---

