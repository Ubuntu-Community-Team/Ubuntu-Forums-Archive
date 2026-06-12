---
title: "Connect to Unbuntu and FTP Server from outside network?"
date: 2009-12-09
forum: General Help
---

### Post by shawn.bordeaux on 2009-12-09
[COLOR=black][FONT=Verdana]Let me start off by saying I am extremely new to ubuntu and fairly new to networking in general. I have setup the vsftpd FTP server on the box and it is running fine. I can connect to it inside my network without any issues. When I try to access it from outside the network (over the internet) it will not connect. I added in some SSL lines to the bottom and I am trying to connect using ftpes security. [/FONT][/COLOR]

[COLOR=black][FONT=Verdana]I am assuming I will need to forward a port or activate a port for it to listen on but I am not sure. Below is my configuration file for vsftpd. I would appreciate any guidance.[/FONT][/COLOR]

```

[COLOR=black][FONT=Verdana]# The default compiled in settings are fairly paranoid. This sample file[/FONT][/COLOR]
[FONT=Verdana][COLOR=black]# loosens things up a bit, to make the ftp daemon more usable.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Please see vsftpd.conf.5 for all compiled in defaults.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# READ THIS: This example file is NOT an exhaustive list of vsftpd options.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# capabilities.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Run standalone? vsftpd can run either from an inetd or as a standalone[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# daemon started from an initscript.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]listen=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Run standalone with IPv6?[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Like the listen parameter, except vsftpd will listen on an IPv6 socket[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# instead of an IPv4 one. This parameter and the listen parameter are mutually[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# exclusive.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#listen_ipv6=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Allow anonymous FTP? (Beware - allowed by default if you comment this out).[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]anonymous_enable=NO[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Uncomment this to allow local users to log in.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]local_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Uncomment this to enable any form of FTP write command.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]write_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Default umask for local users is 077. You may wish to change this to 022,[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# if your users expect that (022 is used by most other ftpd's)[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#local_umask=022[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Uncomment this to allow the anonymous FTP user to upload files. This only[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# has an effect if the above global write enable is activated. Also, you will[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# obviously need to create a directory writable by the FTP user.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#anon_upload_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Uncomment this if you want the anonymous FTP user to be able to create[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# new directories.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#anon_mkdir_write_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Activate directory messages - messages given to remote users when they[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# go into a certain directory.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]dirmessage_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Activate logging of uploads/downloads.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]xferlog_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Make sure PORT transfer connections originate from port 20 (ftp-data).[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]connect_from_port_20=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# If you want, you can arrange for uploaded anonymous files to be owned by[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# a different user. Note! Using "root" for uploaded files is not[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# recommended![/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#chown_uploads=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#chown_username=whoever[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# You may override where the log file goes if you like. The default is shown[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# below.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#xferlog_file=/var/log/vsftpd.log[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# If you want, you can have your log file in standard ftpd xferlog format[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#xferlog_std_format=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# You may change the default value for timing out an idle session.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#idle_session_timeout=600[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# You may change the default value for timing out a data connection.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#data_connection_timeout=120[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# It is recommended that you define on your system a unique user which the[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# ftp server can use as a totally isolated and unprivileged user.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#nopriv_user=ftpsecure[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Enable this and the server will recognise asynchronous ABOR requests. Not[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# recommended for security (the code is non-trivial). Not enabling it,[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# however, may confuse older FTP clients.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#async_abor_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# By default the server will pretend to allow ASCII mode but in fact ignore[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# the request. Turn on the below options to have the server actually do ASCII[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# mangling on files when in ASCII mode.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Beware that on some FTP servers, ASCII support allows a denial of service[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# predicted this attack and has always been safe, reporting the size of the[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# raw file.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# ASCII mangling is a horrible feature of the protocol.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#ascii_upload_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#ascii_download_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# You may fully customise the login banner string:[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#ftpd_banner=Welcome to blah FTP service.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# You may specify a file of disallowed anonymous e-mail addresses. Apparently[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# useful for combatting certain DoS attacks.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#deny_email_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# (default follows)[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#banned_email_file=/etc/vsftpd.banned_emails[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# You may restrict local users to their home directories. See the FAQ for[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# the possible risks in this before using chroot_local_user or[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# chroot_list_enable below.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#chroot_local_user=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# You may specify an explicit list of local users to chroot() to their home[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# directory. If chroot_local_user is YES, then this list becomes a list of[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# users to NOT chroot().[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#chroot_list_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# (default follows)[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#chroot_list_file=/etc/vsftpd.chroot_list[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# You may activate the "-R" option to the builtin ls. This is disabled by[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# default to avoid remote users being able to cause excessive I/O on large[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# the presence of the "-R" option, so there is a strong case for enabling it.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#ls_recurse_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Debian customization[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Some of vsftpd's settings don't fit the Debian filesystem layout by[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# default. These settings are more Debian-friendly.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# This option should be the name of a directory which is empty. Also, the[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# directory should not be writable by the ftp user. This directory is used[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# as a secure chroot() jail at times vsftpd does not require filesystem[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# access.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]secure_chroot_dir=/var/run/vsftpd[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# This string is the name of the PAM service vsftpd will use.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]pam_service_name=vsftpd[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# This option specifies the location of the RSA certificate to use for SSL[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# encrypted connections.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# This option specifies the location of the RSA key to use for SSL[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# encrypted connections.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#enable ssl info[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]ssl_enable=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]allow_anon_ssl=NO[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]force_local_data_ssl=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]force_local_logins_ssl=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]ssl_tlsv1=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]ssl_sslv2=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]ssl_sslv3=YES[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Filezilla uses port 21 if you don't set any port[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# in Servertype "FTPES - FTP over explicit TLS/SSL"[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Port 990 is the default used for FTPS protocol.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]# Uncomment it if you want/have to use port 990.[/COLOR][/FONT]
[FONT=Verdana][COLOR=black]#listen_port=990[/COLOR][/FONT]
 

```

---

### Post by bodhi.zazen on 2009-12-09
You need to access your router and forward port 21 to your ftp server.

---

### Post by shawn.bordeaux on 2009-12-09
Okay, so I forward port 21 to the internal IP of the FTP server than? Thank you for the quick response!

---

### Post by bodhi.zazen on 2009-12-09
> **shawn.bordeaux said:**
> Okay, so I forward port 21 to the internal IP of the FTP server than? Thank you for the quick response!

yes, that should do the trick.

You may need to forward port 20 and 22 as well (I am not sure with vsftpd)

---

### Post by shawn.bordeaux on 2009-12-16
Thank you! That worked!

---

