---
title: "samba troubles two processes"
date: 2010-10-04
forum: General Help
---

### Post by ulao on 2010-10-04
Today my samba did not work, so I first tried restarting it but that didnt get it, neither did a reboot. So I started to investigate. I noticed in my log I get this:

```

[2010/10/04 09:08:06,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/10/04 09:08:07,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/10/04 09:08:07,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/10/04 09:14:24,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/10/04 09:14:24,  0] lib/pidfile.c:121(pidfile_create)
  ERROR: smbd is already running. File /var/run/samba/smbd.pid exists and process id 1494 is running.
[2010/10/04 09:20:49,  0] lib/util_sock.c:738(write_data)
[2010/10/04 09:20:49,  0] lib/util_sock.c:1491(get_peer_addr_internal)
  getpeername failed. Error was Transport endpoint is not connected
  write_data: write failure in writing to client 0.0.0.0. Error Connection reset by peer
[2010/10/04 09:20:49,  0] smbd/process.c:62(srv_send_smb)
  Error writing 4 bytes to client. -1. (Transport endpoint is not connected)


```

I also see this.

```
ps -C smbd
  PID TTY          TIME CMD
  705 ?        00:00:00 smbd
  783 ?        00:00:00 smbd
 1494 ?        00:00:00 smbd
 1499 ?        00:00:00 smbd
```

on a fresh reboot I see two process running. If I stop smbd I still show extra process. I'm not sure how I got to 4, but I'm pretty sure 2 s bad. Keep in mind I dont have any client connections yet. 

Any ideas how to fix this? I tried to remove all pid and tdb files and that didnt help.

---

### Post by ulao on 2010-10-04
I added the line "smb ports = 445" to the [global] in smb.conf and it fixed it. Something about windows netbois cause issues with out this pot open for sambe. Not sure why out of the blue?

---

