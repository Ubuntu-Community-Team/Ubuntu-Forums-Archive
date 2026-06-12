---
title: "automount remove location"
date: 2010-04-23
forum: General Help
---

### Post by sonicb00m on 2010-04-23
I have a bash script that uses sshfs to remotely mount an SSH directory.

Where should i place this script so it mounts with route privileges?

One consideration is i use VPN so the directory needs to be mounted after openvpn is started. 

How do i do this?

---

### Post by sonicb00m on 2010-04-25
Got this working with a root only permissions

```

sshfs#root@xxxx.com:/var/www /media/sshfs/remote fuse port=2223

```

so i tried this but it appears not to mount although I get no error

```

sshfs#root@xxxx.com:/var/www /media/sshfs/remote fuse port=2223,comment=sshfs,users,noauto,uid=1000,gid=1000,allow_other,reconnect,transform_symlinks     0       0

```

What am i doing wrong?

---

### Post by sonicb00m on 2010-04-25
Oh think it was "noauto", now it seems ok!

---

### Post by sonicb00m on 2010-04-25
Ok the location won't mount automatically on reboot , I get an error during startup and have to press S to skip the mounting. Any ideas why this is?

---

