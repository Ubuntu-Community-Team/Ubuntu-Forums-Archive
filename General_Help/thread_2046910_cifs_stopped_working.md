---
title: "cifs stopped working"
date: 2012-08-23
forum: General Help
---

### Post by buffchick on 2012-08-23
Yesterday our UPS in the server rack blew up and all servers lost power. After restoring power I am unable to mount windows shares that were working previously. I've googled like crazy but I'm not really finding anything. Suggestions?

Ubuntu 10.04.4 LTS server

```
itadmin@SVR1:~$ sudo mount -t cifs  //SVR2/home/Bioinformatics /hdrive -o username=user,password=pass,rw

mount error: cifs filesystem not supported by the system
mount error(19): No such device
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
itadmin@SVR1:~$

itadmin@SVR1:/$ sudo modprobe cifs
FATAL: Module .ignore_install not found.
FATAL: Error running install command for cifs
itadmin@SVR1:/$ uname -r
2.6.32-41-server
```names and passwords changed to protect the innocent

---

### Post by buffchick on 2012-08-24
18 hours later.... anyone?

---

### Post by buffchick on 2012-08-24
apt-get purge libwbclient0 samba-common samba-common-bin. apt-get -f install. apt-get install samba. Now I get the following error.
```
itadmin@SVR1:/var/log# mount -t cifs //SVR2/NGS /data -o pass=pass,user=user
mount: unknown filesystem type 'cifs'
```

*edit: oops. forgot to install smbfs. Now I'm back to the original error.*

---

### Post by bootedguy on 2012-08-24
If you are using the latest version of smbfs, you may want to go back to the version you were using before.

---

### Post by buffchick on 2012-08-27
I was using the latest version before.

---

### Post by afoin on 2012-08-27
You could try with the previous kernel , could be interesting.

---

### Post by Borcco on 2012-08-27
:p

---

### Post by buffchick on 2012-08-28
I can't be interesting. This is a production HPC cluster for DNA/Genome sequencing.

---

### Post by buffchick on 2012-08-28
RESOLUTION: After purge and reinstall of samba/cifs/winbind - in /etc/modeprobe.d/cifs.conf
```
# Created to fix cifs, thanks to the ubuntu forums
install cifs /sbin/modprobe .ignore-install cifs && echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled && echo 0 > /proc/fs/cifs/OplockEnabled
remove cifs /sbin/modprobe -r cifs
```change the dot in install cifs /sbin/modprobe .ignore-install to a dash.
```
install cifs /sbin/modprobe -ignore-install cifs && echo 0 > /proc/fs/cifs/LinuxExtensionsEnabled && echo 0 > /proc/fs/cifs/OplockEnabled
remove cifs /sbin/modprobe -r cifs
```

---

