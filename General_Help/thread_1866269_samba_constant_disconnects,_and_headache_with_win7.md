---
title: "samba constant disconnects, and headache with win7"
date: 2011-10-21
forum: General Help
---

### Post by sandrodz on 2011-10-21
I've a problem with Windows 7 Samba/Ubuntu Server connectivity.
  When I first start the Windows machine, I can map the network drive  without issues. But after a while of inactivity it disconnects and almost all the time  gives me error when reconnecting. After that the only way to get back  the connection is to disconnect map, restart windows and it will  automatically work again! 
  It's driving me nuts. 



  From ubuntu laptop this never happens, I simply browser workgroup share from networks.


any ideas??


I've tried win7 forum, askubuntu, superuser, stackoverflow - nobody seems to even answer me.


:popcorn:

---

### Post by satanselbow on 2011-10-21
And the exact error is? Your logs look like? What else have you done to trace the error?

Try and help people help you and an answer may turn up. You wont find many people on forums willing to play guessing games. 

I'm only replying cos I am in a queue and got bored. Wouldn't normally bother when there is so little to go on ;-)

---

### Post by sandrodz on 2011-10-21
> **satanselbow said:**
> And the exact error is? Your logs look like? What else have you done to trace the error?

Try and help people help you and an answer may turn up. You wont find many people on forums willing to play guessing games. 

I'm only replying cos I am in a queue and got bored. Wouldn't normally bother when there is so little to go on ;-)
Thanks for at least dropping a line :)

Anyhow, on windows side error is minimal - it just states that host is unreachable. Or just says nothing and red cross is displayed on the drives.

samba side / I checked the logs, and there is nothing particular or strange going on...

testparm says:

```
testparm
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[torrents]"
Processing section "[dropbox]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
        security = SHARE
        log file = /var/log/samba/log.%m
        name resolve order = bcast wins host
        dns proxy = No
        create mask = 0644
        hosts allow = 10.27.332.31
        hosts deny = 0.0.0.0/0

[torrents]
        comment = torrents
        path = /media/sd/torrents
        read only = No
        guest ok = Yes

[dropbox]
        comment = dropbox
        path = /media/sd/dropbox
        read only = No
        guest ok = Yes


```

config file looks like this:

```
[global]
workgroup = WORKGROUP
netbios name = mini
security = share
encrypt passwords = yes
smb passwd file = /etc/samba/smbpasswd
log file = /var/log/samba/log.%m
dns proxy = No

#sets the necessary permissions on upload
create mask = 0644
directory mask = 0755

#time interval after which samba disconnects due to inactivity, 0 is never.
deadtime = 0

wins support = no
name resolve order = bcast wins host

```

smbd:
```
[2011/10/21 14:30:09.673526,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/10/21 14:30:29.690822,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/10/21 14:46:17.742913,  1] smbd/server.c:267(remove_child_pid)
  Scheduled cleanup of brl and lock database after unclean shutdown
[2011/10/21 14:46:37.745193,  1] smbd/server.c:240(cleanup_timeout_fn)
  Cleaning up brl and lock database after unclean shutdown
[2011/10/21 14:57:34,  0] smbd/server.c:1123(main)
  smbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/21 14:57:34.255347,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/10/21 14:57:34.273422,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/10/21 14:57:34.276655,  0] smbd/server.c:1169(main)
  standard input is not a socket, assuming -D option
[2011/10/21 16:34:41,  0] smbd/server.c:1123(main)
  smbd version 3.5.8 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2010
[2011/10/21 16:34:41.686725,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/10/21 16:34:41.698770,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/10/21 16:34:41.708854,  0] smbd/server.c:1169(main)
  standard input is not a socket, assuming -D option


```

nmbd
```
[2011/10/21 17:30:46.334317,  0] nmbd/nmbd_incomingdgrams.c:308(process_local_master_announce)
  process_local_master_announce: Server FRA-PC at IP 10.57.132.233 is announcing itself as a local master brows$
[2011/10/21 17:30:46.334740,  0] nmbd/nmbd_become_lmb.c:148(unbecome_local_master_success)
  *****

  Samba name server MINI has stopped being a local master browser for workgroup WORKGROUP on subnet 10.57.132.2$

  *****
[2011/10/21 17:31:03.353982,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****

  Samba name server MINI is now a local master browser for workgroup WORKGROUP on subnet 10.57.132.234

  *****
[2011/10/21 17:31:51.612841,  0] nmbd/nmbd_incomingdgrams.c:308(process_local_master_announce)
  process_local_master_announce: Server FRA-PC at IP 10.57.132.233 is announcing itself as a local master brows$
[2011/10/21 17:31:51.613321,  0] nmbd/nmbd_become_lmb.c:148(unbecome_local_master_success)
  *****

  Samba name server MINI has stopped being a local master browser for workgroup WORKGROUP on subnet 10.57.132.2$

  *****
[2011/10/21 17:32:08.640893,  0] nmbd/nmbd_become_lmb.c:395(become_local_master_stage2)
  *****

```

user.log
```
2011/10/21 17:32:11.746859,  1] smbd/service.c:1070(make_connection_snum)
  sandro-pc (10.57.132.235) connect to service dropbox initially as user nobody (uid=65534, gid=65534) (pid 1513)
[2011/10/21 17:32:11.754020,  1] smbd/service.c:1070(make_connection_snum)
  sandro-pc (10.57.132.235) connect to service torrents initially as user nobody (uid=65534, gid=65534) (pid 1513)
[2011/10/21 17:35:11.829333,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2011/10/21 17:35:11.836760,  0] printing/print_cups.c:108(cups_connect)
  Unable to connect to CUPS server localhost:631 - Connection refused

```



This is the only line that could be a hint... but couldn't find much on internet about the error. Just that bunch of guyz see it.

```
[2011/10/21 14:46:17.731130,  0] lib/util_sock.c:1441(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  read_fd_with_timeout: client 0.0.0.0 read error = Connection timed out.

```

---

