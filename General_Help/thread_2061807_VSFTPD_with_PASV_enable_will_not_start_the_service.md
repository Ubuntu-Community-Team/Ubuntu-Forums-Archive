---
title: "VSFTPD with PASV enable will not start the service"
date: 2012-09-23
forum: General Help
---

### Post by hiflyer on 2012-09-23
I recently install version 12 of Ubuntu
I lost my previous configuration file for vsftpd which I had working.
if I do not set pasv_enable=YES the service starts and works ok.
Now when I set pasv_enable=YES the vsftpd will not start (or stay started).

Conf files is
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to blah FTP service.
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=ftp
rsa_cert_file=/etc/ssl/private/vsftpd.pem

pasv_enable=YES 
pasv_addr_resolve=NO
pasv_address=192.168.1.151
pasv_min_port=12000
pasv_max_port=12100

If I do not enable pasv, the service starts and seems to work 
if I enable pasv then after a service vsftpd start (or restart)
followed by service vsftpd status I find 
vsftpd stop/waiting

what am I missing that is required here.
I do have the firewall set to enable FTP (not that should make any difference to the service).:confused:

syslog reports
Sep 23 12:07:06 linux-server kernel: [434811.240122] init: vsftpd main process (9581) terminated with status 1
Sep 23 12:07:06 linux-server kernel: [434811.240193] init: vsftpd respawning too fast, stopped

nothing in vsftpd.log

---

### Post by hiflyer on 2012-09-24
dont know what is wrong but switched to sftp and it seems to work fine thru the router and firewall.

guess I am dumping ftp.

---

