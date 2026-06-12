---
title: "Proftpd Woes"
date: 2010-10-29
forum: General Help
---

### Post by tommycahir on 2010-10-29
Hi Guys

I am a newbie to setting up FTP so I took the cheats way out and used gadmin-proftpd to set-up my config file. 
I couldn't get GADMIN-PROFTPD to activate so I activated it using sudo /etc/init.d/proftpd start
Now when I have proftpd started from the terminal command line and go to [http://ftp://192.168.1.100:21/]("http://ftp//192.168.1.100:21/") in firefox I get a white browser window but no directory listings without any promtp for a username or password
(192.168.1.100 being my internal LAN server IP address)

Can you please tell me what I am doing wrong with the below config? 
```
LoadModule mod_tls.c
ServerType standalone
DefaultServer on
Umask 022
ServerName "192.168.1.100"
ServerIdent on "Aragorn FTP Server"
ServerAdmin [EMAIL="tommycahir@gmail.com"]tommycahir@gmail.com[/EMAIL]
IdentLookups off
UseReverseDNS off
Port 21
PassivePorts 49149 65534
#MasqueradeAddress None
TimesGMT off
MaxInstances 30
MaxLoginAttempts 3
TimeoutLogin 300
TimeoutNoTransfer 120
TimeoutIdle 120
DisplayLogin welcome.msg
DisplayChdir .message
User tommy
Group tommy
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
TLSEngine off
TLSRequired off
TLSVerifyClient off
TLSProtocol SSLv23
TLSLog /var/log/proftpd_tls.log
TLSRSACertificateFile /etc/gadmin-proftpd/certs/cert.pem
TLSRSACertificateKeyFile /etc/gadmin-proftpd/certs/key.pem
TLSCACertificateFile /etc/gadmin-proftpd/certs/cacert.pem
TLSRenegotiate required off
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
  AllowUser ftpmovies
  AllowUser tommy
  DenyALL
</Limit>

<Anonymous /media/sdb1/Movies>
User ftpmovies
Group FTPUSERS
AnonRequirePassword off
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>

<Anonymous /media/sdb1/Movies>
User tommy
Group FTPUSERS
AnonRequirePassword on
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  SITE  MTDM  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE_CHMOD  SITE_CHGRP >
 DenyAll
</Limit>
<Directory /root/Documents>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Directory>
</Anonymous>
```BTW I have also included my proftp version info below:

```
tommy@aragorn:~$ proftpd -V
Compile-time Settings:
  Version: 1.3.2c (maint)
  Platform: LINUX
  Built: Tue Dec 22 14:02:40 UTC 2009
  Built With:
    configure  '--prefix=/usr' '--with-includes=/usr/include/postgresql:/usr/include/mysql' '--mandir=/usr/share/man' '--sysconfdir=/etc/proftpd' '--localstatedir=/var/run' '--libexecdir=/usr/lib/proftpd' '--enable-sendfile' '--enable-facl' '--enable-dso' '--enable-autoshadow' '--enable-ctrls' '--with-modules=mod_readme' '--enable-ipv6' '--enable-nls' '--build' 'x86_64-linux-gnu' '--with-shared=mod_unique_id:mod_site_misc:mod_load:mod_ban:mod_quotatab:mod_sql:mod_sql_mysql:mod_sql_postgres:mod_sql_sqlite:mod_sql_odbc:mod_dynmasq:mod_quotatab_sql:mod_ldap:mod_quotatab_ldap:mod_ratio:mod_tls:mod_rewrite:mod_radius:mod_wrap:mod_wrap2:mod_wrap2_file:mod_wrap2_sql:mod_quotatab_file:mod_quotatab_radius:mod_facl:mod_ctrls_admin:mod_ifsession' 'build_alias=x86_64-linux-gnu' 'CFLAGS=-O2 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -DHAVE_OPENSSL -DUSE_LDAP_TLS ' 'LDFLAGS=-Wl,-Bsymbolic-functions' 'CPPFLAGS=' 'CXXFLAGS=-g -O2' 'FFLAGS=-g -O2'

  CFLAGS: -O2 -D_LARGEFILE64_SOURCE -D_FILE_OFFSET_BITS=64 -DHAVE_OPENSSL -DUSE_LDAP_TLS  -Wall
  LDFLAGS: -L$(top_srcdir)/lib -Wl,-Bsymbolic-functions
  LIBS: -lacl  -lssl -lcrypto -lcap  -lpam -lsupp -lcrypt 

  Files:
    Configuration File:
      /etc/proftpd/proftpd.conf
    Pid File:
      /var/run/proftpd.pid
    Scoreboard File:
      /var/run/proftpd/proftpd.scoreboard
    Header Directory:
      /usr/include/proftpd
    Shared Module Directory:
      /usr/lib/proftpd

  Features:
    + Autoshadow support
    + Controls support
    + curses support
    - Developer support
    + DSO support
    + IPv6 support
    + Largefile support
    - Lastlog support
    + ncurses support
    + NLS support
    + OpenSSL support
    + POSIX ACL support
    + Shadow file support
    + Sendfile support
    + Trace support

  Tunable Options:
    PR_TUNABLE_BUFFER_SIZE = 1024
    PR_TUNABLE_GLOBBING_MAX = 8
    PR_TUNABLE_HASH_TABLE_SIZE = 40
    PR_TUNABLE_NEW_POOL_SIZE = 512
    PR_TUNABLE_SCOREBOARD_BUFFER_SIZE = 80
    PR_TUNABLE_SCOREBOARD_SCRUB_TIMER = 30
    PR_TUNABLE_SELECT_TIMEOUT = 30
    PR_TUNABLE_TIMEOUTIDENT = 10
    PR_TUNABLE_TIMEOUTIDLE = 600
    PR_TUNABLE_TIMEOUTLINGER = 30
    PR_TUNABLE_TIMEOUTLOGIN = 300
    PR_TUNABLE_TIMEOUTNOXFER = 300
    PR_TUNABLE_TIMEOUTSTALLED = 3600
    PR_TUNABLE_XFER_SCOREBOARD_UPDATES = 10
```I am sure it is something really simple but I am lost!

Thanks for any help or advice given..

---

### Post by tommycahir on 2010-11-09
Nobody able to help with this at all?

---

### Post by SlugSlug on 2010-11-09
what do you want? A password  login to FTP for a local account, and jailed to home can be done by using this config 

```
# This is a basic ProFTPD configuration file (rename it to 
# 'proftpd.conf' for actual use.  It establishes a single server
# and a single anonymous login.  It assumes that you have a user/group
# "nobody" and "ftp" for normal operation and anon.

ServerName "Alpha Vision Design Secure FTP Server"
ServerType            standalone
DefaultServer            on

# Allow FTP resuming.
# Remember to set to off if you have an incoming ftp for upload.
AllowStoreRestart off

# Port 21 is the standard FTP port.
Port 21

# Umask 022 is a good standard umask to prevent new dirs and files
# from being group and world writable.
Umask                022

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd).
MaxInstances            30

# Set the user and group under which the server will run.
User                nobody
Group                nogroup

# To cause every FTP user to be "jailed" (chrooted) into their home
# directory, uncomment this line.
DefaultRoot ~

# Normally, we want files to be overwriteable.
AllowOverwrite        on

# Bar use of SITE CHMOD by default
#<Limit SITE_CHMOD>
#  DenyAll
#</Limit>

# Needed for NIS.

PersistentPasswd off

# Default root can be used to put users in a chroot environment.
# As an example if you have a user foo and you want to put foo in /home/foo
# chroot environment you would do this:
#
DefaultRoot ~

<Global>
  DenyFilter \*.*/
DefaultRoot ~
</Global>


RootLogin off
AllowForeignAddress off
AllowRetrieveRestart on
DirFakeUser off nobody
LogFormat auth "%v [%P] %h %t "%r" %s"
Extendedlog /var/log/proftpd/ftp.log
UseReverseDNS off
LogFormat default "%h %l %u %t "%r" %s %b"
SystemLog /var/log/proftpd/proftpd.log
DisplayConnect /etc/banner-proftpd
DirFakeGroup off nobody
DeleteAbortedStores off
IdentLookups off
DeferWelcome on
TimesGMT off
TransferLog /var/log/proftpd/xferlog
AccessGrantMsg " -- Guest access granted for %u --"
ServerIdent off
LogFormat write "%h %l %u %t "%r" %s %b"
AccessDenyMsg " !-!! Here Be Dragons !!-! "


```

---

### Post by tommycahir on 2010-11-15
Hi [SlugSlug]("http://ubuntuforums.org/member.php?u=716956")

Thanks a million for the help it has come in very useful and as a result I managed to figure out that some other program was already using port 21 ??? [not sure what though]

```
Nov 15 18:29:50 aragorn proftpd[11004] aragorn: Failed binding to ::, port 1021: Address already in use
Nov 15 18:29:50 aragorn proftpd[11004] aragorn: Check the ServerType directive to ensure you are configured correctly.

```My next question is now how do I allow a user access to only a specific directory e.g Movies, is it something like the below that gadmin-proftpd generated?

```
<Anonymous /media/sdb1/Movies>
User ftpmovies
Group FTPUSERS
AnonRequirePassword off
MaxClients 10 "The server is full, hosting %m users"
DisplayLogin welcome.msg
<Limit LOGIN>
Allow from all
Deny from all
</Limit>
<Limit LIST NLST  RETR  PWD XPWD  SIZE  STAT  CWD XCWD  CDUP XCUP >
 AllowAll
</Limit>
<Limit STOR STOU  APPE  RNFR RNTO  DELE  MKD XMKD SITE_MKDIR  RMD XRMD SITE_RMDIR  SITE  SITE_CHMOD  SITE_CHGRP  MTDM >
 DenyAll
</Limit>
</Anonymous>
```

---

