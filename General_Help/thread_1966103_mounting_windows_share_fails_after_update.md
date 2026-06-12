---
title: "mounting windows share fails after update"
date: 2012-04-26
forum: General Help
---

### Post by buffchick on 2012-04-26
ubuntu 10.04 LTS. windows share was mounted for the past several months by:
```
sudo mount -t smbfs //WINSERVER1/D$ /mount -o user=user,pass=password,,dir_mode=0775,gid=1009,noperm
```

Ran update on 4/20. Did a system reboot last night and now can no longer mount the share. Get the following error
```
[71857.863045] Status code returned 0xc000006d NT_STATUS_LOGON_FAILURE
[71857.863056]  CIFS VFS: Send error in SessSetup = -13
[71857.863072]  CIFS VFS: cifs_mount failed w/return code = -13

```

The share is a local share on a windows XP machine and is not on a domain. The windows 7 shares that are on the domain are working fine. We created a test local share on a windows 7 machine and it works fine. I have no idea what to do next. Is there any way to rollback? is there some secret password encryption I don't know about that changed? Where can you look to see if bugs have been reported? I'm going crazy. Please help! :D

---

### Post by buffchick on 2012-04-27
Bumping this up because still trying to find an answer.

---

### Post by buffchick on 2012-05-01
was a DNS issue totally unrelated to samba... :|

---

