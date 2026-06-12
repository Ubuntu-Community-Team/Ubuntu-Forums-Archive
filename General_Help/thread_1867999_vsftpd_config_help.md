---
title: "vsftpd config help"
date: 2011-10-23
forum: General Help
---

### Post by The Sorrow on 2011-10-23
Im needing some help with vsftpd. I have the service running and (hopefully) configured correctly with a chroot jail. The jail works. all i get when i go up a directory is [ftp://10.10.2.100/../../../](ftp://10.10.2.100/../../../).... and so on.

I want the ftp files to be in /opt/vsftpd (otherwise just tell me where they go by default). As it is the root directory for the ftp is empty...

Here is the config: 
```

listen=YES
anonymous_enable=YES
local_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
idle_session_timeout=600
ftpd_banner=TheLair's FTP
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/vsftpd.pem
listen_port=21
local_root=/opt/vsftpd
anon_root=/opt/vsftpd

```

IRONY!
Right as i posted this it began to work. Mods can close this at any time.

---

