---
title: "sftp sending my users to root directory"
date: 2010-12-03
forum: General Help
---

### Post by rectifiercc on 2010-12-03
Hi there,
I have an ftp server and normal login works fine as well as ftps but for some reason sftp sends all my accounts to the root directory of the entire server (not good). Been searching around but can't find a fix. Anyone encounter this?
I'm using ubuntu 9.10 and proftpd

thx

---

### Post by Verbeck on 2010-12-03
could you post the config file
from a terminal (application>accessories>terminal), run the following command and post the output here
```

cat /etc/proftpd/proftpd.conf

```

---

### Post by rectifiercc on 2010-12-03
```
LoadModule mod_tls.c
ServerType standalone
DefaultServer on
Umask 022
ServerName "myserver.com"
ServerIdent on "myserver.com"
ServerAdmin info@myserver.com
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User nobody
Group nobody
DirFakeUser off nobody
DirFakeGroup off nobody
#DefaultRoot ~
DefaultTransferMode binary
AllowForeignAddress off
AllowRetrieveRestart on
AllowStoreRestart on
DeleteAbortedStores off
TransferRate RETR 220
TransferRate STOR 250
TransferRate STOU 250
TransferRate APPE 250
SystemLog /var/log/secure
RequireValidShell off
Include /etc/proftpd/tls.conf
#<IfModule mod_tls.c>
#TLSEngine on
#TLSRequired off
#TLSVerifyClient off
#TLSProtocol SSLv23
#TLSLog /var/log/proftpd_tls.log
#TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
#TLSRSACertificateFile /etc/gadmin-proftpd/certs/proftpd.crt
#TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
#TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/proftpd.key
#TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
#TLSRenegotiate required off
#</IfModule>
<IfModule mod_ratio.c>
Ratios off
SaveRatios off
RatioFile "/restricted/proftpd_ratios"
RatioTempFile "/restricted/proftpd_ratios_temp"
CwdRatioMsg "Please upload first!"
FileRatioErrMsg "FileRatio limit exceeded, upload something first..."
ByteRatioErrMsg "ByteRatio limit exceeded, upload something first..."
LeechRatioMsg "Your ratio is unlimited."
</IfModule>
<Limit LOGIN>
  AllowUser WN-photo
  AllowUser knud
  AllowUser webcam
  AllowUser Bruce
  AllowUser rec2
  AllowUser rec
  DenyALL
</Limit>

<Anonymous /var/www/Shared/photos/upload>
User WN-photo
Group group1
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
 Allow from all
 Deny from all
</Limit>
AllowOverwrite off
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/www/Shared/Bryan>
User knud
Group group1
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /media/Data-Drive/Images/Webcams/Webcam-Image>
User webcam
Group group1
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/www/Shared/Bruce>
User Bruce
Group group1
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/www/web-acess>
User rec2
Group group1
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /media/>
User rec
Group group1
AnonRequirePassword on
MaxClients 5 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
AllowOverwrite on
<Limit LIST NLST  STOR STOU  APPE  RETR  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit NOTHING >
 DenyAll
</Limit>
</Anonymous>

```

---

### Post by rectifiercc on 2010-12-03
Here is the tls.conf code as well:
```
#
# Proftpd sample configuration for FTPS connections.
#
# Note that FTPS impose some limitations in NAT traversing.
# See http://www.castaglia.org/proftpd/doc/contrib/ProFTPD-mini-HOWTO-TLS.html
# for more information.
#

<IfModule mod_tls.c>
TLSEngine                               on
TLSLog                                  /var/log/proftpd/tls.log
TLSProtocol                             SSLv23
#TLSOptions                 NoCertRequest
#
# Server SSL certificate. You can generate a self-signed certificate using 
# a command like:
#
# openssl req -x509 -newkey rsa:1024 \
#          -keyout /etc/ssl/private/proftpd.key -out /etc/ssl/certs/proftpd.crt \
#          -nodes -days 365
#
# The proftpd.key file must be readable by root only. The other file can be
# readable by anyone.
#
# chmod 0600 /etc/ssl/private/proftpd.key 
# chmod 0640 /etc/ssl/private/proftpd.key
# 
#TLSRSACertificateFile                   /etc/ssl/certs/proftpd.crt
TLSRSACertificateFile                   /etc/proftpd/ssl/proftpd.cert.pem
#TLSRSACertificateKeyFile                /etc/ssl/private/proftpd.key
TLSRSACertificateKeyFile                /etc/proftpd/ssl/proftpd.key.pem

#
# CA the server trusts
#TLSCACertificateFile 			 /etc/ssl/certs/CA.pem
# or avoid CA cert
TLSOptions                              NoCertRequest
#
# Authenticate clients that want to use FTP over TLS?
#
TLSVerifyClient                         off
#
# Are clients required to use FTP over TLS when talking to this server?
#
TLSRequired                             off
#
# Allow SSL/TLS renegotiations when the client requests them, but
# do not force the renegotations.  Some clients do not support
# SSL/TLS renegotiations; when mod_tls forces a renegotiation, these
# clients will close the data connection, or there will be a timeout
# on an idle data connection.
#
TLSRenegotiate                          required off
</IfModule>

```

---

### Post by Verbeck on 2010-12-03
try un-commenting *DefaultRoot ~*
and change ~ to where you want the users to be eg, /home/ftpserver (~ is for the home directory of the user if it exists on the system)
then restart proftpd
```

sudo /etc/init.d/proftpd restart
```

---

### Post by rectifiercc on 2010-12-03
that didn't work either. I actually had tried that before and I tried again on your suggestion. All the users are where they're supposed to be when I select "normal" or "ftps" in my ftp clients (filezilla and fetch I'm using) but when I try connecting using sftp it takes them all to the root of my whole system. Doh! Thx for your input. :-)

---

### Post by zeero_k on 2010-12-13
I don't have a specific solution for you, but I do know that SFTP connections are handled by sshd, not proftpd. (Try stopping proftpd and see what happens when you connect!)

So, you will want to tinker with your /etc/ssh/sshd_config file.
I'm guessing that you can set some sort of chroot restriction per user, to accomplish what you want.

Sorry I don't have more specific help, I'm scrambling to fix another issue...

   ~0K

---

