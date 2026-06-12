---
title: "VSFTPD behind modem and router"
date: 2012-09-26
forum: General Help
---

### Post by jasonlyle88 on 2012-09-26
I currently have the following setup: I have a cable modem that has a router hooked up directly to it and then all devices go through that router.  My Ubuntu Server is also behind that router.  When i go to use FTP through filezilla, i can't connect using my external IP address.  Below are the logs from both filezilla and vsftpd as well as my vsftpd.conf file.  Any insight as to what is going wrong or how to fix this would be greatly appreciated.

I have my modem set to treat my router as the DMZ and i have ports 20, 21, and 50000-51000 forwarded from my router to my ubuntu box for FTP.

I think the problem might have to do something with the IP address being changed to a different address on the 227 Entering PASV mode response.  You can see the differences near the end of each of the log files. 

I have changed the IP addresses in the below information for security reasons and have replaced them with the following stand in information:
External IP Address: E1.E2.E3.E4
Modem IP Address: M1.M2.M3.M4
Router IP Address: R1.R2.R3.R4

Server Log:
```

Wed Sep 26 03:52:33 2012 [pid 2] CONNECT: Client "E1.E2.E3.E4"
Wed Sep 26 03:52:33 2012 [pid 2] FTP response: Client "E1.E2.E3.E4", "220 (vsFTPd 2.3.5)"
Wed Sep 26 03:52:33 2012 [pid 2] FTP command: Client "E1.E2.E3.E4", "USER jlyle"
Wed Sep 26 03:52:33 2012 [pid 2] [jlyle] FTP response: Client "E1.E2.E3.E4", "331 Please specify the password."
Wed Sep 26 03:52:33 2012 [pid 2] [jlyle] FTP command: Client "E1.E2.E3.E4", "PASS <password>"
Wed Sep 26 03:52:33 2012 [pid 1] [jlyle] OK LOGIN: Client "E1.E2.E3.E4"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", "230 Login successful."
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP command: Client "E1.E2.E3.E4", "SYST"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", "215 UNIX Type: L8"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP command: Client "E1.E2.E3.E4", "FEAT"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", "211-Features:"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", " EPRT??"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", " EPSV??"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", " MDTM??"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", " PASV??"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", " REST STREAM??"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", " SIZE??"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", " TVFS??"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", " UTF8??"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", "211 End"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP command: Client "E1.E2.E3.E4", "OPTS UTF8 ON"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", "200 Always in UTF8 mode."
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP command: Client "E1.E2.E3.E4", "PWD"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", "257 "/home/jlyle""
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP command: Client "E1.E2.E3.E4", "TYPE I"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", "200 Switching to Binary mode."
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP command: Client "E1.E2.E3.E4", "PASV"
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP response: Client "E1.E2.E3.E4", "227 Entering Passive Mode (E1,E2,E3,E4,195,194)."
Wed Sep 26 03:52:33 2012 [pid 3] [jlyle] FTP command: Client "E1.E2.E3.E4", "LIST"

```
Filezilla Log:
```

Status:	Connecting to E1.E2.E3.E4:21...
Status:	Connection established, waiting for welcome message...
Response:	220 (vsFTPd 2.3.5)
Command:	USER jlyle
Response:	331 Please specify the password.
Command:	PASS ********
Response:	230 Login successful.
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 EPRT
Response:	 EPSV
Response:	 MDTM
Response:	 PASV
Response:	 REST STREAM
Response:	 SIZE
Response:	 TVFS
Response:	 UTF8
Response:	211 End
Command:	OPTS UTF8 ON
Response:	200 Always in UTF8 mode.
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/home/jlyle"
Command:	TYPE I
Response:	200 Switching to Binary mode.
Command:	PASV
Response:	227 Entering Passive Mode (M1,M2,M3,M4,195,98)
Status:	Server sent passive reply with unroutable address. Using server address instead.
Command:	LIST

```

VSFTPD config file:
```

# Example config file /etc/vsftpd.conf
#
# The default compiled in settings are fairly paranoid. This sample file
# loosens things up a bit, to make the ftp daemon more usable.
# Please see vsftpd.conf.5 for all compiled in defaults.
#
# READ THIS: This example file is NOT an exhaustive list of vsftpd options.
# Please read the vsftpd.conf.5 manual page to get a full idea of vsftpd's
# capabilities.
#
#
# Run standalone?  vsftpd can run either from an inetd or as a standalone
# daemon started from an initscript.
listen=YES
#
# Run standalone with IPv6?
# Like the listen parameter, except vsftpd will listen on an IPv6 socket
# instead of an IPv4 one. This parameter and the listen parameter are mutually
# exclusive.
#listen_ipv6=YES
#
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
#
# Uncomment this to enable any form of FTP write command.
write_enable=YES
#
# Default umask for local users is 077. You may wish to change this to 022,
# if your users expect that (022 is used by most other ftpd's)
#local_umask=022
#
# Uncomment this to allow the anonymous FTP user to upload files. This only
# has an effect if the above global write enable is activated. Also, you will
# obviously need to create a directory writable by the FTP user.
#anon_upload_enable=YES
#
# Uncomment this if you want the anonymous FTP user to be able to create
# new directories.
#anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
#
# If enabled, vsftpd will display directory listings with the time
# in  your  local  time  zone.  The default is to display GMT. The
# times returned by the MDTM FTP command are also affected by this
# option.
use_localtime=YES
#
# Activate logging of uploads/downloads.
xferlog_enable=YES
#
# Make sure PORT transfer connections originate from port 20 (ftp-data).
connect_from_port_20=YES
#
# If you want, you can arrange for uploaded anonymous files to be owned by
# a different user. Note! Using "root" for uploaded files is not
# recommended!
#chown_uploads=YES
#chown_username=whoever
#
# You may override where the log file goes if you like. The default is shown
# below.
#xferlog_file=/var/log/vsftpd.log
#
# If you want, you can have your log file in standard ftpd xferlog format.
# Note that the default log file location is /var/log/xferlog in this case.
#xferlog_std_format=YES
#
# You may change the default value for timing out an idle session.
#idle_session_timeout=600
#
# You may change the default value for timing out a data connection.
#data_connection_timeout=120
#
# It is recommended that you define on your system a unique user which the
# ftp server can use as a totally isolated and unprivileged user.
#nopriv_user=ftpsecure
#
# Enable this and the server will recognise asynchronous ABOR requests. Not
# recommended for security (the code is non-trivial). Not enabling it,
# however, may confuse older FTP clients.
#async_abor_enable=YES
#
# By default the server will pretend to allow ASCII mode but in fact ignore
# the request. Turn on the below options to have the server actually do ASCII
# mangling on files when in ASCII mode.
# Beware that on some FTP servers, ASCII support allows a denial of service
# attack (DoS) via the command "SIZE /big/file" in ASCII mode. vsftpd
# predicted this attack and has always been safe, reporting the size of the
# raw file.
# ASCII mangling is a horrible feature of the protocol.
#ascii_upload_enable=YES
#ascii_download_enable=YES
#
# You may fully customise the login banner string:
#ftpd_banner=Welcome to blah FTP service.
#
# You may specify a file of disallowed anonymous e-mail addresses. Apparently
# useful for combatting certain DoS attacks.
#deny_email_enable=YES
# (default follows)
#banned_email_file=/etc/vsftpd.banned_emails
#
# You may restrict local users to their home directories.  See the FAQ for
# the possible risks in this before using chroot_local_user or
# chroot_list_enable below.
#chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
# (Warning! chroot'ing can be very dangerous. If using chroot, make sure that
# the user does not have write access to the top level directory within the
# chroot)
#chroot_local_user=YES
#chroot_list_enable=YES
# (default follows)
#chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
# Customization
#
# Some of vsftpd's settings don't fit the filesystem layout by
# default.
#
# This option should be the name of a directory which is empty.  Also, the
# directory should not be writable by the ftp user. This directory is used
# as a secure chroot() jail at times vsftpd does not require filesystem
# access.
secure_chroot_dir=/var/run/vsftpd/empty
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/private/vsftpd.pem

log_ftp_protocol=YES
pasv_address=E1.E2.E3.E4
pasv_min_port=50000
pasv_max_port=51000

```

---

