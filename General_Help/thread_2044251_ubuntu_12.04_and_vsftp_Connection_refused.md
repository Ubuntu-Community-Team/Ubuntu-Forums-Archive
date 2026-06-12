---
title: "ubuntu 12.04 and vsftp: Connection refused"
date: 2012-08-19
forum: General Help
---

### Post by alain.roger on 2012-08-19
Hi,

i read a lot of posts on internet about how to configure vsFTPd under Ubuntu 12.04. My first try was to make it works for anonymous access.

so i did everything to allow local user to connect via ftp localhost of ftp + ip address, but everytime i get the error message "connection refused"

i tried to find where is my mistake but i didn't find it.
any help would be great, thx.

here is the /etc/vsftpd.conf:
```
listen=YES
anonymous_enable=YES 
local_enable=YES
write_enable=YES
anon_upload_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
```

if i check open port with nmap localhost i get:
```
Starting Nmap 5.21 ( http://nmap.org ) at 2012-08-19 09:57 CEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00037s latency).
Not shown: 996 closed ports
PORT     STATE SERVICE
53/tcp   open  domain
80/tcp   open  http
631/tcp  open  ipp
3306/tcp open  mysql
```

if i use nmap + ip address ( e.g. 192.168.163.128 ) i get just 1 port:
```
Starting Nmap 5.21 ( http://nmap.org ) at 2012-08-19 09:59 CEST
Nmap scan report for 192.168.163.128
Host is up (0.00034s latency).
Not shown: 999 closed ports
PORT   STATE SERVICE
80/tcp open  http

```

---

### Post by Merrattic on 2012-08-19
Here's mine that works:

```
#custom vsftpd.conf
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
local_umask=022
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to Server FTP service.
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
```

---

