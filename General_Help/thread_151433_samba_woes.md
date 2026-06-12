---
title: "samba woes"
date: 2006-03-27
forum: General Help
---

### Post by b4t3m4n on 2006-03-27
I have just installed 5.10 onto a machine using the "server" install.  I have updated the few out of date packages, installed apache, mysql and samba.  I have properly setup the smb.conf file to share a folder on the computer, I have done it multiple times before on various linux distro's using samba.  This is the error I get when I try to connect to the share.  Any help would be appreciated.


```
[2006/03/27 21:50:39, 0] lib/util_sock.c:open_socket_in(708)
[2006/03/27 21:50:39, 0] smbd/oplock.c:init_oplocks(1357)
  open_oplock_ipc: Failed to get local UDP socket for address 100007f. Error was 
  Cannot assign requested address
```

---

