---
title: "FTP on Port 21"
date: 2011-03-28
forum: General Help
---

### Post by czerdrill on 2011-03-28
Having an issue connecting with FTP...I use Filezilla and my server has vsftp as its ftp server.  I can connect through filezilla using port 22, but port 21 just gives me a connection timed out error.  How am I supposed to configure it so that my users can connect with regular ftp on port 21, and not only SFTP.  The reason I want to do this is because I am unable to chroot someone into their home directory using vsftp.  Nothing seems to work when I try to do this...

---

### Post by newbuntuxx on 2011-03-28
Is your vsftp behind a router/firewall?

Do you have ubuntu firewall enabled?

What is your vsftp config like?

Can you connect to your vsftp from the local machine? like this:

```
ftp localhost
```

run:
```
sudo tcpdump port 20 or 21
```

While thats running, try to connect to port 21 and see what the tcpdump shows.

---

### Post by czerdrill on 2011-03-28
How do I check if ubuntu firewall is enabled?  

My vsftpd.conf file is as follows:

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
# chroot_local_user=YES
#
# You may specify an explicit list of local users to chroot() to their home
# directory. If chroot_local_user is YES, then this list becomes a list of
# users to NOT chroot().
#chroot_local_user=NO
chroot_list_enable=YES
# (default follows)
chroot_list_file=/etc/vsftpd.chroot_list
#
# You may activate the "-R" option to the builtin ls. This is disabled by
# default to avoid remote users being able to cause excessive I/O on large
# sites. However, some broken FTP clients such as "ncftp" and "mirror" assume
# the presence of the "-R" option, so there is a strong case for enabling it.
#ls_recurse_enable=YES
#
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
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
userlist_enable=YES
```

the tcpdump just freezes until I press Ctrl-C to end it.  It doesn't show anything else happening.

---

### Post by czerdrill on 2011-03-28
As an update, when I do a netstat for port 21, I show that vsftpd is listening on it, so doesn't that mean it should work?  However, through filezilla or any other FTP client I get a connection timed out when I try port 21.  Port 22 works with no problem.

If someone can tell me how to fix port 21, OR, how to properly chroot someone it would be great.  As it stands now, all my users are able to see every part of my server, even though I set their homes differently...

---

### Post by newbuntuxx on 2011-03-28
In terminal run:

```
ftp localhost
```

Post output

Also run:
```
service vsftpd status
```

Post output

Just to be clear, you need to run the tcpdump command first and leave it running, and then try and connect via port 21. If the tcpdump command shows nothing, it means that the connection is not even getting to your server. Which is why I asked you:

> Is your vsftp behind a router/firewall?


The tcpdump command shows any connections that hit your network card on port 20 or 21. If nothing is hitting your card on those ports, then that traffic is being blocked elsewhere.

To check for ubuntu firewall run:

```
sudo ufw status
```

---

### Post by czerdrill on 2011-03-28
Thanks for your continued help with this...here is the outputs:

ftp localhost:

```
connected to localhost.localdomain.
220(vsFTPd 2.2.0)
Name (localhost:name):
```service vsftpd status:

```
vsftpd is running
```sudo ufw status:

shows that it's active and lists a bunch of ports including port 22 as being ALLOW from Anywhere.  It does not however show port 21...so could this be it?

and finally the tcpdump gives the connection timed out error when I try to connect while it's running.  Once I close the connection it says:

```
Flags [S], seq 1698045827, win 5480 options [mss 1460, sackOK, TS value 54285 ecr 0, nop, wscale 6], length 0

3 packets captured
3 packets received by filter
0 packets dropped by kernel
```Any ideas?

---

### Post by czerdrill on 2011-03-29
bump...

---

### Post by newbuntuxx on 2011-03-30
Yes. The firewall is dropping your ftp traffic.

Run:

```
sudo ufw allow from any to any port 21
```

The rule basically allows connections from ANY IP address to port 21

---

### Post by czerdrill on 2011-03-30
> **newbuntuxx said:**
> Yes. The firewall is dropping your ftp traffic.

Run:

```
sudo ufw allow from any to any port 21
```The rule basically allows connections from ANY IP address to port 21

Perfect!  Thanks so much for your help.  Now the only thing that remains is that some users are given a Permission denied when trying to ftp.  I checked permissions and on the users that are getting permission denied, their chrooted folders are owned by root.  Is it as simple as changing their ownership to their username and would it be:

```
chown username:group -R folder
```

or is it some other command?

---

### Post by newbuntuxx on 2011-03-30
Yes. chown will do the trick. You got the command right. 

Let me know if it works.

---

### Post by czerdrill on 2011-03-30
> **newbuntuxx said:**
> Yes. chown will do the trick. You got the command right. 

Let me know if it works.

Hmm nope didn't work.  I changed permissions correctly and verified it with ls -al, but no go.  Still get permission denied for one user.  The other users work perfectly, can FTP through 21, and also they are chrooted to their home directories.

---

### Post by czerdrill on 2011-03-30
interesting update.  for that one user, i can still use port 22 to get in with no issue, but they are not chrooted.  port 21 gives permission denied in filezilla, could not connect to server

---

### Post by czerdrill on 2011-03-30
ok what i did was just created a new user and they were chrooted correctly on port 21, so that problem is solved.  Why are they not chrooted on port 22 though?  They can still go up and down directories, all the way up to root...

---

