---
title: "cant get proftpd working on ubuntu 11.04"
date: 2011-08-15
forum: General Help
---

### Post by tetsu7 on 2011-08-15
im trying to get an ftp server running with gadmin proftpd on ubuntu 11.04. ive installed it many times and keep getting an error about postgresql so ive tried uninstalling and reinstalling postgresql but when i do the reinstall i get the same messege as when i installed proftpd_ **E: gforge-shell-postgresql: subprocess installed post-installation script returned error exit status 1**_ below is what i got from synaptic after reinstalling postgresql. after that is my proftpd .conf file as it is now. ive changed it so many times trying everything i can find online over the past 2 days and still i cant get it to work. any help with getting proftpd working would be greatly appreciated! thank you!

**synaptic messege after reinstalling postgresql:**
(Reading database ... 203186 files and directories currently installed.)
Preparing to replace postgresql 8.4.8-0ubuntu0.11.04 (using .../postgresql_8.4.8-0ubuntu0.11.04_all.deb) ...
Unpacking replacement postgresql ...
Setting up gforge-shell-postgresql (5.0.2-5) ...
Calculating defaults
Reading defaults from /etc/fusionforge/fusionforge.conf
Creating /etc/fusionforge/fusionforge.conf
SSL Disabled
Creating /etc/gforge/httpd.conf
Creating /etc/gforge/httpd.secrets
Creating /etc/gforge/local.inc
Creating other includes
Installing chroot environnement at /var/lib/gforge/chroot
............................
cp: cannot stat `/lib/libgcc_s*': No such file or directory
dpkg: error processing gforge-shell-postgresql (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Setting up postgresql (8.4.8-0ubuntu0.11.04) ...
Errors were encountered while processing:
 gforge-shell-postgresql
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up gforge-shell-postgresql (5.0.2-5) ...
Calculating defaults
Reading defaults from /etc/fusionforge/fusionforge.conf
Creating /etc/fusionforge/fusionforge.conf
SSL Disabled
Creating /etc/gforge/httpd.conf
Creating /etc/gforge/httpd.secrets
Creating /etc/gforge/local.inc
Creating other includes
Installing chroot environnement at /var/lib/gforge/chroot
............................
cp: cannot stat `/lib/libgcc_s*': No such file or directory
dpkg: error processing gforge-shell-postgresql (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 gforge-shell-postgresql


**Gadmin-proftpd-1.3.3D .conf:**
ModulePath /usr/lib/proftpd
LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c
LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
LoadModule mod_dynmasq.c
LoadModule mod_vroot.c
LoadModule mod_ifsession.c
ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.0.106"
ServerIdent on "My FTP Server"
ServerAdmin [email]email@example.org[/email]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49152 65534
MasqueradeAddress 192.168.0.1
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
<IfModule mod_tls.c>
TLSEngine on
TLSRequired off
TLSVerifyClient on
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
TLSOptions AllowClientRenegotiation
</IfModule>
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
  AllowUser  anonymous
  AllowUser tetsu
  DenyALL
</Limit>

<Anonymous /var/FTP/anonymous>
User  anonymous
Group  anonymous
AnonRequirePassword off
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayChdir .msg
<Limit LOGIN>
Allow from All
Deny from all
</Limit>
AllowOverwrite off
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /var/FTP>
User tetsu
Group group1
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
DisplayChdir .msg
<Limit LOGIN>
Allow from All
Deny from all
</Limit>
AllowOverwrite off
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

---

### Post by requeth on 2011-08-15
[http://www.debian-administration.org/articles/251](http://www.debian-administration.org/articles/251)

Follow the above instructions and you can remove the debris that's causing your install to fail.

---

### Post by tetsu7 on 2011-08-16
thanks! that took care of my gforge-shell-postgresql problem however im getting a 530 login incorrect when i tey to login to my ftp server. does anyone have any suggestions for me? heres my current .conf

# To really apply changes reload proftpd after modifications.
AllowOverwrite on
AuthAliasOnly on

# Choose here the user alias you want !!!!
UserAlias lordofthenexus userftp

ServerName            "TheNexus"
ServerType             standalone
DeferWelcome            on

MultilineRFC2228 on
DefaultServer            on
ShowSymlinks            off

TimeoutNoTransfer 600
TimeoutStalled 100
TimeoutIdle 2200

DisplayChdir                    .message
ListOptions                    "-l"

RequireValidShell         off

TimeoutLogin 20

RootLogin             off

# It's better for debug to create log files ;-)
ExtendedLog             /var/log/ftp.log
TransferLog             /var/log/xferlog
SystemLog            /var/log/syslog.log

#DenyFilter            \*.*/

# I don't choose to use /etc/ftpusers file (set inside the users you want to ban, not useful for me)
UseFtpUsers off

# Allow to restart a download
AllowStoreRestart        on

# Port 21 is the standard FTP port, so you may prefer to use another port for security reasons (choose here the port you want)
Port                21

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 8

# Set the user and group that the server normally runs at.
User                  nobody
Group                 nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask                022    022

PersistentPasswd        off

MaxClients 8
MaxClientsPerHost 8
MaxClientsPerUser 8
MaxHostsPerUser 8

# Display a message after a successful login
AccessGrantMsg "welcome !!!"
# This message is displayed for each access good or not
ServerIdent                  on       "you're at home"

# Lock all the users in home directory, ***** really important *****
DefaultRoot ~

MaxLoginAttempts    5

#VALID LOGINS
<Limit LOGIN>
AllowUser userftp
DenyALL
</Limit>

<Directory /home/FTP-shared>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNRF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/FTP-shared/download/*>
Umask 022 022
AllowOverwrite off
    <Limit MKD STOR DELE XMKD RNEF RNTO RMD XRMD>
    DenyAll
    </Limit>
</Directory>

<Directory /home/FTP-shared/upload/>
Umask 022 022
AllowOverwrite on
    <Limit READ RMD DELE>
          DenyAll
        </Limit>

        <Limit STOR CWD MKD>
          AllowAll
        </Limit>
</Directory>

<IfModule mod_tls.c>
    TLSEngine on
    TLSLog /var/ftpd/tls.log
    TLSProtocol TLSv1

    # Are clients required to use FTP over TLS when talking to this server?
    TLSRequired off

    # Server's certificate
    TLSRSACertificateFile /etc/ftpcert/server.crt
    TLSRSACertificateKeyFile /etc/ftpcert/server.key

    # CA the server trusts
    TLSCACertificateFile /etc/ftpcert/ca.crt

    # Authenticate clients that want to use FTP over TLS?
    TLSVerifyClient off
</IfModule>

---

### Post by tetsu7 on 2011-08-16
I found the error, I put the conf in /etc/ instead of /etc/proftpd/.

---

