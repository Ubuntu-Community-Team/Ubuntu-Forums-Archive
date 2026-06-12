---
title: "Sever Can't Join Windows Domain"
date: 2006-04-11
forum: General Help
---

### Post by kozmo on 2006-04-11
I have installed Samba, but when I enter the command:
**net rpc join -D DOMAIN_NAME -U admin_user**

I get the error:

brockj@msgsapjy3yr11lin:/home$ net rpc join -D DOMHOME -U brockj
[2006/04/11 14:52:45, 0] passdb/secrets.c:secrets_init(63)
  Failed to open /var/lib/samba/secrets.tdb
[2006/04/11 14:52:45, 0] utils/net_rpc.c:rpc_oldjoin_internals(266)
  error storing domain sid for DOMHOME
Password:
[2006/04/11 14:52:53, 0] utils/net_rpc_join.c:net_rpc_join_newstyle(319)
  Error domain join verification (reused connection): STATUS_BUFFER_OVERFLOW

Unable to join domain DOMHOME.

Here is my smb.conf file:

[global]
   security = domain
   workgroup = DOMHOME
   netbios name = MSGSAPJY3YR11LIN
   encrypt passwords = yes
   log level = 2
   syslog = 2
   log file = /var/log/samba/log.%m
   max log size = 1000
   os level = 0
   preferred master = no
   domain master = no
   local master = no
   wins server = 129.52.62.111
   wins support = no
   password server = *
   server string = Ubuntu Linux [%h]
   bind interfaces only = yes
   interfaces = 127.0.0.1 129.52.62.76
    deadtime = 30
   max smbd processes = 64
   template homedir = /home/%D/%U
   template shell = /bin/bash

I have created the directory /home/DOMHOME
and chmod of 775 for this directory.

Any suggestions?

---

### Post by mr_widget on 2006-07-28
change security = ads

---

