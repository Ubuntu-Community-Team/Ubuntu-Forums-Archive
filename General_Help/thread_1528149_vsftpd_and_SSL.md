---
title: "vsftpd and SSL"
date: 2010-07-10
forum: General Help
---

### Post by Jimoid on 2010-07-10
Hi,

On Ubuntu 8.10 I have installed vsftpd and configured it to use SSL, and created a self signed SSL certificate. When I attempt to login using FireFTP, Firefox is unable to find the server's certificate.

I have imported the .pem certificate manually but Firefox still tries to find the certificate. Does anyone know what I'm doing wrong?

Cheers

```
root@mail2:~# cat /etc/vsftpd.conf 
# disables anonymous FTP
anonymous_enable=NO
# enables non-anonymous FTP
local_enable=YES
# activates virtual users
guest_enable=YES
# virtual users to use local privs, not anon privs
virtual_use_local_privs=YES
# enables uploads and new directories
write_enable=YES
# the PAM file used by authentication of virtual uses
pam_service_name=vsftpd-virtual
# in conjunction with 'local_root',
# specifies a home directory for each virtual user
user_sub_token=$USER
local_root=/var/www/html/$USER
# the virtual user is restricted to the virtual FTP area
chroot_local_user=YES
# hides the FTP server user IDs and just display "ftp" in directory listings
hide_ids=YES
# runs vsftpd in standalone mode
listen=YES
# listens on this port for incoming FTP connections
listen_port=21
# the minimum port to allocate for PASV style data connections
pasv_min_port=62222
# the maximum port to allocate for PASV style data connections
pasv_max_port=63333
# controls whether PORT style data connections use port 20 (ftp-data)
connect_from_port_20=YES
# the umask for file creation
local_umask=022


ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=YES
force_local_logins_ssl=YES

ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

rsa_cert_file=/etc/vsftpd/vsftpd.pem
```


SSL certificate created with:

```
root@mail2:~# /usr/bin/openssl req -x509 -nodes -days 3650 -newkey rsa:1024 -keyout vsftpd.pem -out vsftpd.pem

```

---

