---
title: "vsftpd"
date: 2009-08-27
forum: General Help
---

### Post by serpantman on 2009-08-27
Could someone post a copy of their vsftpd.conf. I deleted mine thinking reinstalling vsftp would restore it. Ive been have a lot of trouble with it for some reason. I set it up when i was 15 on red hat, but it's not working today :S.

---

### Post by jonobr on 2009-08-27
I made some minor changes myself but hopefully this will get you going


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
#write_enable=YES
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
anon_mkdir_write_enable=YES
#
# Activate directory messages - messages given to remote users when they
# go into a certain directory.
dirmessage_enable=YES
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
# If you want, you can have your log file in standard ftpd xferlog format
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
ftpd_banner=Welcome , Please use this in accordance with XXXXXX Policies and procedures. Act the Mick, and Ill kick your *****!!!
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
secure_chroot_dir=/var/run/vsftpd
#
# This string is the name of the PAM service vsftpd will use.
pam_service_name=vsftpd
#
# This option specifies the location of the RSA certificate to use for SSL
# encrypted connections.
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
# This option specifies the location of the RSA key to use for SSL
# encrypted connections.
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

```

---

### Post by serpantman on 2009-08-27
500 OOPS: cannot open user list file:/etc/vsftpd.user_list

I guess im missing this too? Can someone post theirs also. It looks like i really messed things up.

EDIT: i checked, the file doesnt exist, thats the problem

---

### Post by jonobr on 2009-08-27
mmm....
Try changing the following lines

```
# Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=NO
#
# Uncomment this to allow local users to log in.
local_enable=YES
```

to


> # Allow anonymous FTP? (Beware - allowed by default if you comment this out).
anonymous_enable=YES
#
# Uncomment this to allow local users to log in.
#local_enable=YES

Does that work?>

---

### Post by jonobr on 2009-08-27
Also you may want to change the banner login message

---

### Post by serpantman on 2009-08-27
i had already changed those 3 options, otherwise its the exact same i beleive, this in configured to run from init correct?

do you not have a copy of that file either?

---

### Post by jonobr on 2009-08-27
No i dont, :(

---

### Post by serpantman on 2009-08-27
i just made a empty file with that name and it works now, but i get this when trying to use the ls command

226 Transfer done (but failed to open directory).

EDIT: /home/ftp is 744

---

### Post by serpantman on 2009-08-27
Commented out this 

#secure_chroot_dir=/var/run/vsftpd

Didnt work. 

/home/ftp is owned by root? shoudl be changed to ftp? same with the files in it?

---

### Post by serpantman on 2009-08-27
chown ftp /ftp/home

made this happen

500 OOPS: vsftpd: refusing to run with writable anonymous root

not sure why that would happen. these are the permissions

drwxr--r--  2 ftp    root     4096 2009-08-27 14:30 ftp

---

### Post by serpantman on 2009-08-27
sudo chmod 077 /home/ftp

and back to this. Same with 477.

226 Transfer done (but failed to open directory).

---

### Post by jonobr on 2009-08-27
Are you running Selinux?

If you got to /etc/
is there a folder called selinux?

---

### Post by serpantman on 2009-08-27
Nope. Are you as stumped as i am? Its weird cause vsftp is supposed to be really easy, i've used it before. You just setup config and restart it. 

One thing i noticed now though, is when restarting i get this 

 * Stopping FTP server: vsftpd                                                  No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
 * Starting FTP server: vsftpd                                           [ OK ] 



and i have to restart with sudo or i get this

 * Stopping FTP server: vsftpd                                                  No /usr/sbin/vsftpd found running; none killed.
                                                                         [ OK ]
rm: cannot remove `/var/run/vsftpd/vsftpd.pid': Permission denied

---

### Post by serpantman on 2009-08-27
When i logon as user, which im pretty sure i have turned off. I can ls, but this happens when trying to get

ftp> get S6300315.AVI
local: S6300315.AVI remote: S6300315.AVI
local: S6300315.AVI: Permission denied

---

### Post by serpantman on 2009-08-27
I commented out anon, and still logged in as anon. Something is wrong here, you config you gave me is for stand alone or init.d? I starting it with init.d, if i try to run sudo vsftpd i get


500 OOPS: could not bind listening IPv4 socket


Something is very wrong, im not sure what i did, maybe im connecting to a different ftpd then vsftp?

EDIT: yes i remembered to restart it

---

### Post by serpantman on 2009-08-27
im not getting my welcome message :(

---

### Post by jonobr on 2009-08-27
Yes I am.


I thought as you mentioned the removal using synaptic and reinstallation,
should pretty much have done it and Im a bit lost.
The Selinux came from a google search for your exact problem.

Im thinking , scr3w ftp and move to ssh, if you install openssh from synaptic you get a far more secure transfer protocol with some error recover capability.

WOuld you be willing to try out SSH/SCP?

---

### Post by serpantman on 2009-08-27
Definetly.

---

### Post by jonobr on 2009-08-27
you could try downloading openssh from synaptic,

When it installs you can use winscp from a windows box or command line or places-> connect to server from an ubuntu box..

I think that will sort you

---

### Post by PascalGR on 2009-09-19
Hi all,

I've setted up vsftpd to my development linux box and I want to have some accounts to be allowed to ftp and chroot'ed to their specific locations. Anonymous logins are restricted. I've searched Google and forums, however my problem remains. Most people face problems with anonymous logins which is not my case. The problem I have is the:
vsftpd: refusing to run with writable anonymous root
message.

My vsftpd.conf has these params enabled:
listen=YES
local_enable=YES
write_enable=YES
dirmessage_enable=YES
xferlog_enable=YES
connect_from_port_20=YES
chroot_local_user=YES
secure_chroot_dir=/var/run/vsftpd
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/certs/ssl-cert-snakeoil.pem
rsa_private_key_file=/etc/ssl/private/ssl-cert-snakeoil.key

The directory I'm trying to ftp has the following permissions:
drwxrwxr-x 13 user1 developer      4096 2009-09-19 18:34 website1

I try to ftp with user1 (home dir /opt/websites/website1) and get this error:
vsftpd: refusing to run with writable anonymous root

Hint: I need all users to belong to the developer group because I need all developer accounts to have access and edit all websites directories.

Any help would be really much appreciated!

---

### Post by Bachstelze on 2009-09-19
You must either disable anonymous logins, or define the root directory for such logins to a directory that is not writable by the ftp user.

---

### Post by PascalGR on 2009-09-19
weird, uncommented the following line and setted it to NO:
anonymous_enable=NO
the message gone but user still could not login. Then I changed the shell from /usr/sbin/nologin to /bin/bash and voila!

Thanks!

---

