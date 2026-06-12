---
title: "Can't connect to Ubuntu via FTP (vsftpd)"
date: 2011-05-17
forum: General Help
---

### Post by Stan* on 2011-05-17
Hi there,

I have installed vsftpd and I configured the whole package and everything worked. But, after a reboot, it doesn't work anymore.
Vsftpd is running. When I do "telnet localhost 21" the machine gets connected to localhost. It also succeeds when I type "192.168.2.10" (my internet IP address) or "86.80.107.30" (external IP address). So the connection is fine.
I configured vsftpd to allow only given users, in this case the user bourne. Everyone else isn't allowed to use vsftpd. My main account is stan. So when I connect to the machine via SSH, I'm logged in as 'stan'. When I try to log in to the FTP server with "ftp localhost" and I fill my own username I get an error message saying permission is denied, I don't get a chance to enter my password. When I fill in the username 'bourne' it asks for a password, I enter it, and I get the message 'login incorrect'.
But now it's getting weird: When I switch to the user bourne in the shell by 'su bourne' and enter the same password for FTP, I get logged in as bourne. Then, when I enter 'ftp localhost', fill in the username 'bourne', enter its password, the login is succesfull!

It doesn't matter where I connect to (local IP, external IP, localhost, or computer name) I get connected with the user bourne as long as I'm logged in to the shell with this user. Otherwise it doesn't work.

Does anyone know why? Below is the config file of vsftpd:

**/etc/vsftpd.conf:**
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
# Allow anonymous FTP? (Disabled by default)
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
#use_localtime=YES
use_localtime=NO
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
xferlog_std_format=YES
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
ftpd_banner=Dit is de back-upserver van Bourne Multimedia (www.madebybourne.com).
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
chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
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
# Debian customization
#
# Some of vsftpd's settings don't fit the Debian filesystem layout by
# default.  These settings are more Debian-friendly.
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

#### Added 16 May 2011 ####
userlist_deny=NO
userlist_enable=YES
userlist_file=/etc/vsftpd.allowed_users
```

**/etc/vsftpd.allowed_users:**
```
bourne
```

Many thanks in advance!

---

### Post by Stan* on 2011-05-17
A miracle has happened! I went for dinner and when I came back everything is working again! I don't know why, I didn't do anything...Man, this is getting weird.

---

### Post by Stan* on 2011-05-18
Well, as you would expect it wasn't a miracle. When I enabled shell access for the FTP user 'bourne' I could login to the server via FTP. When I disabled shell (usermod -s /bin/false bourne), I wasn't.
Now I set the -s parameter to /usr/sbin/nologin and added that line '/usr/sbin/nologin' to /etc/shells. Now the users hasn't shell access _and_ is able to log in to the server.

---

