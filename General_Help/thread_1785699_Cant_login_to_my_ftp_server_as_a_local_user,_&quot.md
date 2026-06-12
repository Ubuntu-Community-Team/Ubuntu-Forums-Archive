---
title: "Cant login to my ftp server as a local user, &quot;530 login incorrect&quot;"
date: 2011-06-18
forum: General Help
---

### Post by friendlybacon on 2011-06-18
I have been trying to figure this out for the past couple hours.

I am using vsftpd, and i am able to login to the ftp server as anonymous  user, but whenever i try to login as a local user, I get the following  error:

Connected to 192.168.0.1.
220 ****************Welcome to Chris's FTP server.**********************
Name (192.168.0.1:chris): chris
331 Please specify the password.
Password:
530 Login incorrect.
Login failed.
ftp> ^Z



My vsftpd config file (found in /etc) is as follows:        

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  ~~~~~~~~~~~~~~~~~~~~~~`


listen=YES
#listen_ipv6=YES
anonymous_enable=YES
local_enable=YES
write_enable=YES
local_umask=000
anon_upload_enable=YES
anon_mkdir_write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
#chown_uploads=YES
#chown_username=whoever
#xferlog_file=/var/log/vsftpd.log
#xferlog_std_format=YES
#idle_session_timeout=600
#data_connection_timeout=120
nopriv_user=ftpsecure
#async_abor_enable=YES
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
ftpd_banner=                                                                                  ****************Welcome to Chris's FTP  server.**********************         
banned_email_file=/etc/vsftpd.banned_emails
#chroot_local_user=YES
#chroot_local_user=YES
#chroot_list_enable=YES
#chroot_list_file=/etc/vsftpd.chroot_list
#ls_recurse_enable=YES
secure_chroot_dir=/var/run/vsftpd/empty
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem

pam_service_name=vsftpd
no_anon_password=YES

~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~  ~~~~~~~~~~~~~~~~~~~~~~~~~~


I could really use some help with this.

Thanks!

---

