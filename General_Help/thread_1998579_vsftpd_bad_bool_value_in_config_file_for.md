---
title: "vsftpd bad bool value in config file for:"
date: 2012-06-07
forum: General Help
---

### Post by nem1tor on 2012-06-07
Running ubuntu 12.04 32 bit
I seem to be stuck on this one. When I try to start vsftpd I get this error:

"bad bool value in config file for: ( here would be whatever the first line on the config file is)"

As you may have guessed I get the same error no matter what the value is.
It maybe something simple that I am just overlooking.

Here is my vsftpd.conf contents:

anonymous_enable=YES
no_anon_password=YES
local_enable=NO
write_enable=YES
local_umask=777
anon_upload_enable=YES
anon_mkdir_write_enable=YES
anon_other_write_enable=NO
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
xferlog_std_format=YES
ftpd_banner=Welcome 
chroot_local_user=NO
guest_enable=NO
listen=NO
listen_port=21
pasv_min_port=40000
pasv_max_port=40999
pam_service_name=vsftpd

---

### Post by nem1tor on 2012-06-08
fixed by complete removal and installed again.

---

