---
title: "vsftpd, pam and virtual users..."
date: 2010-12-13
forum: General Help
---

### Post by aSteve on 2010-12-13
I'm tearing my  hair out... I'm sure something obvious is wrong, but I can't see what.   I've installed vsftpd, and that allowed me to log in using my main  login user-id and password.  Unfortunately, I need to allow ftp access  for an independent set of users to those who I want to grant login...  From a quick web-search, I discovered that virtual users seem to be how  to do this:

[http://howto.gumph.org/content/setup...ies-in-vsftpd/]("http://howto.gumph.org/content/setup-virtual-users-and-directories-in-vsftpd/")

Unfortunately, I don't seem to be able to make this work - the  usernames/passwords in my separate password file are always rejected...  but I know my configuration is having an effect as when I update  /etc/pam.d/vsftpd, my main login user name and password is rejected.

My vsftpd.conf contains:

--
listen=YES
anonymous_enable=NO
local_enable=YES
write_enable=YES
dirmessage_enable=YES
use_localtime=YES
xferlog_enable=YES
connect_from_port_20=YES
ftpd_banner=Welcome to private FTP service
secure_chroot_dir=/var/run/vsftpd/empty
pam_service_name=vsftpd
rsa_cert_file=/etc/ssl/private/vsftpd.pem
virtual_use_local_privs=YES
user_sub_token=$USER
local_root=/var/ftp/$USER
chroot_local_user=YES
hide_ids=YES
ftp_username=nobody
--

my /etc/pam.d/vsftpd contains:

--
# Customized login using htpasswd file
auth    required pam_pwdfile.so pwdfile /etc/vsftpd/passwd
account required pam_permit.so
--

I used htpasswd to create /etc/vsftpd/passwd - which I've tried with permissions of 600 and 644... with the following contents:

--
steve:64Fir0TFZT6Bg
--


The logs show very little of use - the only relevant message in /var/log/auth.log is

--
pam_pwdfile[1]: user not found in password database
--

Any ideas?  On another distribution I've used pureftpd - but it seems  vsftpd is the preferred Ubuntu way... Has anyone successfully configured  vsftpd to work in this way - or is my only option to revert to  pureftpd?

---

### Post by brdido on 2010-12-14
Remeber to erase EVERYTHING else from /etc/pam.d/vsftpd but:

# Customized login using htpasswd file
auth    required pam_pwdfile.so pwdfile /etc/vsftpd/passwd
account required pam_permit.so

---

