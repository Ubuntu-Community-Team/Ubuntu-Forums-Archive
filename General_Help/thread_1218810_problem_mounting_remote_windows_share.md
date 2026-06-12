---
title: "problem mounting remote windows share"
date: 2009-07-21
forum: General Help
---

### Post by Mia_tech on 2009-07-21
guys, I'm using this guide from [ubuntu documentation]("https://help.ubuntu.com/community/MountWindowsSharesPermanently") I'm using the CIFS user method, but when I do "mount -a" this is the error I get

```
sudo mount -a
mount error(13): Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

```

by the way I created the credentials file

```
sudo chown root /root/.smbcredentials
sudo chmod 600 /root/.smbcredentials

```

yet, I'm getting permission errors

---

