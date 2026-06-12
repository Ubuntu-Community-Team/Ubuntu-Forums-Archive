---
title: "proftpd: login OK, can't get directory listing (both active and passive modes)"
date: 2012-06-24
forum: General Help
---

### Post by CbIP on 2012-06-24
Hi all!
I'm trying to set up a proftpd server. And I've faced with one problem.
Everything seems to be working, but when I try to connect to my FTP server, Filezilla shows the following error:
```
Status:	Connecting to 192.168.0.2:21...
Status:	Connection established, waiting for welcome message...
Response:	220 ProFTPD 1.3.4a Server (CbIP FTP) [192.168.0.2]
Command:	USER anonymous
Response:	331 Anonymous login ok, send your complete email address as your password
Command:	PASS **************
Response:	230 Anonymous access granted, restrictions apply
Command:	SYST
Response:	215 UNIX Type: L8
Command:	FEAT
Response:	211-Features:
Response:	 LANG en-US.UTF-8;en-US*
Response:	 MDTM
Response:	 MFMT
Response:	 TVFS
Response:	 UTF8
Response:	 MFF modify;UNIX.group;UNIX.mode;
Response:	 MLST modify*;perm*;size*;type*;unique*;UNIX.group*;UNIX.mode*;UNIX.owner*;
Response:	 SITE MKDIR
Response:	 SITE RMDIR
Response:	 SITE UTIME
Response:	 SITE SYMLINK
Response:	 REST STREAM
Response:	 SITE COPY
Response:	 SIZE
Response:	211 End
Command:	OPTS UTF8 ON
Response:	200 UTF8 set to on
Status:	Connected
Status:	Retrieving directory listing...
Command:	PWD
Response:	257 "/" is the current directory
Command:	TYPE I
Response:	200 Type set to I
Command:	PORT 192,168,0,100,206,11
Response:	200 PORT command successful
Command:	MLSD
Error:	Connection timed out
Error:	Failed to retrieve directory listing
```

This happens both in active and passive modes, in both Filezilla and Opera.
I've googled this problem and found out, that it may be connected with firewall/port forwarding.
But I'm trying to connect from LAN (192.168.0.2 - server; 192.168.0.100 - client) - there is no firewall there.
Also, it looks like, proftpd is started and it listens both active (21) and passive (55555, 55556) ports (I ran netstat when Filezilla was trying to connect):
```
root@CbIP-Server:/home/cbip# netstat -antp
&#1040;&#1082;&#1090;&#1080;&#1074;&#1085;&#1099;&#1077; &#1089;&#1086;&#1077;&#1076;&#1080;&#1085;&#1077;&#1085;&#1080;&#1103; &#1089; &#1080;&#1085;&#1090;&#1077;&#1088;&#1085;&#1077;&#1090;&#1086;&#1084; (servers and established)
Proto Recv-Q Send-Q Local Address Foreign Address State       PID/Program name
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      32010/smbd
tcp        0      0 0.0.0.0:10000           0.0.0.0:*               LISTEN      1352/perl
tcp        0      0 0.0.0.0:32400           0.0.0.0:*               LISTEN      1207/Plex Media Ser
tcp        0      0 0.0.0.0:21              0.0.0.0:*               LISTEN      19277/proftpd: (acc
tcp        0      0 0.0.0.0:32469           0.0.0.0:*               LISTEN      1375/Plex DLNA Serv
tcp        0      0 0.0.0.0:22              0.0.0.0:*               LISTEN      30488/sshd
tcp        0      0 0.0.0.0:38710           0.0.0.0:*               LISTEN      8344/Plex Plug-in [
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      32010/smbd
tcp        0      0 0.0.0.0:53949           0.0.0.0:*               LISTEN      1375/Plex DLNA Serv
tcp        0      0 192.168.0.2:55555       0.0.0.0:*               LISTEN      20434/anon@localhos
tcp        0      0 192.168.0.2:55555       192.168.0.100:52768     SYN_RECV    -
tcp        0    404 192.168.0.2:22          192.168.0.100:52696     ESTABLISHED 18881/sshd: cbip [p
tcp        1      0 127.0.0.1:55660         127.0.0.1:45462         CLOSE_WAIT  1375/Plex DLNA Serv
tcp        0      0 192.168.0.2:445         192.168.0.101:5743      ESTABLISHED 13663/smbd
tcp        0      0 192.168.0.2:445         192.168.0.100:51813     ESTABLISHED 29239/smbd
tcp        0      0 192.168.0.2:21          192.168.0.100:52767     ESTABLISHED 20434/anon@localhos
tcp6       0      0 :::22                   :::*                    LISTEN      30488/sshd

```

My proftpd.log looks like:
```
Jun 24 14:54:57 CbIP-Server proftpd[19277] 127.0.1.1: ProFTPD 1.3.4a (maint) (built Fri Dec 16 2011 17:47:14 UTC) standalone mode STARTUP
Jun 24 14:55:11 CbIP-Server proftpd[19306] 127.0.1.1 (192.168.0.100[192.168.0.100]): FTP session opened.
Jun 24 10:55:11 CbIP-Server proftpd[19306] 127.0.1.1 (192.168.0.100[192.168.0.100]): Preparing to chroot to directory '/mnt/Data/FTP'
Jun 24 10:55:11 CbIP-Server proftpd[19306] 127.0.1.1 (192.168.0.100[192.168.0.100]): ANON ftp: Login successful.
Jun 24 14:56:33 CbIP-Server proftpd[19461] 127.0.1.1 (192.168.0.100[192.168.0.100]): FTP session opened.
Jun 24 10:56:33 CbIP-Server proftpd[19461] 127.0.1.1 (192.168.0.100[192.168.0.100]): Preparing to chroot to directory '/mnt/Data/FTP'
Jun 24 10:56:33 CbIP-Server proftpd[19461] 127.0.1.1 (192.168.0.100[192.168.0.100]): ANON ftp: Login successful.
Jun 24 10:57:36 CbIP-Server proftpd[19461] 127.0.1.1 (192.168.0.100[192.168.0.100]): FTP session closed.
Jun 24 11:05:11 CbIP-Server proftpd[19306] 127.0.1.1 (192.168.0.100[192.168.0.100]): Data transfer stall timeout: 600 seconds
Jun 24 11:05:11 CbIP-Server proftpd[19306] 127.0.1.1 (192.168.0.100[192.168.0.100]): FTP session closed.
Jun 24 15:31:37 CbIP-Server proftpd[20434] 127.0.1.1 (192.168.0.100[192.168.0.100]): FTP session opened.
Jun 24 11:31:38 CbIP-Server proftpd[20434] 127.0.1.1 (192.168.0.100[192.168.0.100]): Preparing to chroot to directory '/mnt/Data/FTP'
Jun 24 11:31:38 CbIP-Server proftpd[20434] 127.0.1.1 (192.168.0.100[192.168.0.100]): ANON ftp: Login successful.
```

/var/log/proftpd/xferlog is empty

Also, I added this to fix the passive mode issue:
```
UseIPv6				off
UseReverseDNS off
PassivePorts                  55555 55556
MasqueradeAddress		192.168.0.2
```

My proftpd.conf:
```
#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes, reload proftpd after modifications, if
# it runs in daemon mode. It is not required in inetd/xinetd mode.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				off
UseReverseDNS off

# If set on you can experience a longer connection delay in many cases.
IdentLookups			off
TimeoutLinger 0

ServerName			"CbIP FTP"
ServerType standalone
DeferWelcome			off

MultilineRFC2228 on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer 600
TimeoutStalled 600
TimeoutIdle 1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
DefaultRoot			~

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
RequireValidShell		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
PassivePorts                  55555 55556

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
MasqueradeAddress		192.168.0.2
# This is useful for masquerading address with dynamic IPs:
# refresh any configured MasqueradeAddress directives every 8 hours
<IfModule mod_dynmasq.c>
# DynMasqRefresh 28800
</IfModule>

# To prevent DoS attacks, set the maximum number of child processes
# to 30.  If you need to allow more than 30 concurrent connections
# at once, simply increase this value.  Note that this ONLY works
# in standalone mode, in inetd mode you should use an inetd server
# that allows you to limit maximum number of processes per service
# (such as xinetd)
MaxInstances 30

# Set the user and group that the server normally runs at.
User				proftpd
Group				nogroup

# Umask 022 is a good standard umask to prevent new files and dirs
# (second parm) from being group and world writable.
Umask				022  022
# Normally, we want files to be overwriteable.
AllowOverwrite			on

# Uncomment this if you are using NIS or LDAP via NSS to retrieve passwords:
# PersistentPasswd		off

# This is required to use both PAM-based authentication and local passwords
# AuthOrder			mod_auth_pam.c* mod_auth_unix.c

# Be warned: use of this directive impacts CPU average load!
# Uncomment this if you like to see progress and transfer rate with ftpwho
# in downloads. That is not needed for uploads rates.
#
# UseSendFile			off

TransferLog /var/log/proftpd/xferlog
SyslogLevel debug
SystemLog /var/log/proftpd/proftpd.log

# Logging onto /var/log/lastlog is enabled but set to off by default
#UseLastlog on

# In order to keep log file dates consistent after chroot, use timezone info
# from /etc/localtime.  If this is not set, and proftpd is configured to
# chroot (e.g. DefaultRoot or <Anonymous>), it will use the non-daylight
# savings timezone regardless of whether DST is in effect.
#SetEnv TZ :/etc/localtime

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# http://www.securityfocus.com/bid/11430/discuss
# It is on by default. 
<IfModule mod_delay.c>
DelayEngine on
</IfModule>

<IfModule mod_ctrls.c>
ControlsEngine        off
ControlsMaxClients    2
ControlsLog           /var/log/proftpd/controls.log
ControlsInterval      5
ControlsSocket        /var/run/proftpd/proftpd.sock
</IfModule>

<IfModule mod_ctrls_admin.c>
AdminControlsEngine off
</IfModule>

#
# Alternative authentication frameworks
#
#Include /etc/proftpd/ldap.conf
#Include /etc/proftpd/sql.conf

#
# This is used for FTPS connections
#
#Include /etc/proftpd/tls.conf

#
# Useful to keep VirtualHost/VirtualRoot directives separated
#
#Include /etc/proftpd/virtuals.con

# A basic anonymous configuration, no upload directories.

 <Anonymous ~ftp>
   User				ftp
   Group			ftp
   # We want clients to be able to login with "anonymous" as well as "ftp"
   UserAlias			anonymous ftp
   # Cosmetic changes, all files belongs to ftp user
   DirFakeUser	on ftp
   DirFakeGroup on ftp
 
   RequireValidShell		off
 
   # Limit the maximum number of anonymous logins
   MaxClients			10
 
   # We want 'welcome.msg' displayed at login, and '.message' displayed
   # in each newly chdired directory.
   DisplayLogin			welcome.msg
   DisplayChdir		.message
 
   # Limit WRITE everywhere in the anonymous chroot
   <Directory *>
     <Limit WRITE>
       DenyAll
     </Limit>
   </Directory>
 
    #Uncomment this if you're brave.
    <Directory upload>
      # Umask 022 is a good standard umask to prevent new files and dirs
      # (second parm) from being group and world writable.
      Umask				022  022
               <Limit READ WRITE>
               DenyAll
               </Limit>
               <Limit STOR>
               AllowAll
               </Limit>
    </Directory>
 
 </Anonymous>

# Include other custom configuration files
Include /etc/proftpd/conf.d/

```

And my modules.conf:
```
#
# This file is used to manage DSO modules and features.
#

# This is the directory where DSO modules reside

ModulePath /usr/lib/proftpd

# Allow only user root to load and unload modules, but allow everyone
# to see which modules have been loaded

ModuleControlsACLs insmod,rmmod allow user root
ModuleControlsACLs lsmod allow user *

LoadModule mod_ctrls_admin.c
LoadModule mod_tls.c

# Install one of proftpd-mod-mysql, proftpd-mod-pgsql or any other
# SQL backend engine to use this module and the required backend.
# This module must be mandatory loaded before anyone of
# the existent SQL backeds.
#LoadModule mod_sql.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_ldap.c

#
# 'SQLBackend mysql' or 'SQLBackend postgres' (or any other valid backend) directives 
# are required to have SQL authorization working. You can also comment out the
# unused module here, in alternative.
#

# Install proftpd-mod-mysql and decomment the previous
# mod_sql.c module to use this.
#LoadModule mod_sql_mysql.c

# Install proftpd-mod-pgsql and decomment the previous 
# mod_sql.c module to use this.
#LoadModule mod_sql_postgres.c

# Install proftpd-mod-sqlite and decomment the previous
# mod_sql.c module to use this
#LoadModule mod_sql_sqlite.c

# Install proftpd-mod-odbc and decomment the previous
# mod_sql.c module to use this
#LoadModule mod_sql_odbc.c

# Install one of the previous SQL backends and decomment 
# the previous mod_sql.c module to use this
#LoadModule mod_sql_passwd.c

LoadModule mod_radius.c
LoadModule mod_quotatab.c
LoadModule mod_quotatab_file.c

# Install proftpd-mod-ldap to use this
#LoadModule mod_quotatab_ldap.c

# Install one of the previous SQL backends and decomment 
# the previous mod_sql.c module to use this
#LoadModule mod_quotatab_sql.c
LoadModule mod_quotatab_radius.c
LoadModule mod_wrap.c
LoadModule mod_rewrite.c
LoadModule mod_load.c
LoadModule mod_ban.c
LoadModule mod_wrap2.c
LoadModule mod_wrap2_file.c
# Install one of the previous SQL backends and decomment 
# the previous mod_sql.c module to use this
#LoadModule mod_wrap2_sql.c
LoadModule mod_dynmasq.c
LoadModule mod_exec.c
LoadModule mod_shaper.c
LoadModule mod_ratio.c
LoadModule mod_site_misc.c

LoadModule mod_sftp.c
LoadModule mod_sftp_pam.c
# Install one of the previous SQL backends and decomment 
# the previous mod_sql.c module to use this
#LoadModule mod_sftp_sql.c

LoadModule mod_facl.c
LoadModule mod_unique_id.c
LoadModule mod_copy.c
LoadModule mod_deflate.c
LoadModule mod_ifversion.c
LoadModule mod_tls_memcache.c

# keep this module the last one
LoadModule mod_ifsession.c


```

Certainly, I have user and group, called 'ftp', it's home directory is set to '/mnt/Data/FTP'

And permissions for '/mnt/Data/FTP' are set to:
```
root@CbIP-Server:/mnt/Data/FTP# ls -la
&#1080;&#1090;&#1086;&#1075;&#1086; 12
drwxr-xr-x 3 ftp  ftp  4096 &#1080;&#1102;&#1085;&#1103;  24 11:56 .
drwxr-xr-x 5 root root 4096 &#1080;&#1102;&#1085;&#1103;  24 13:57 ..
drwxrwxrwx 2 ftp  ftp  4096 &#1080;&#1102;&#1085;&#1103;  24 11:23 upload
```


I need help to fix 'Failed to retrieve directory listing' :)

---

### Post by CbIP on 2012-06-29
Seriously? Nobody knows how to fix this? It's a pity...

---

### Post by CbIP on 2012-06-30
The case is solved!
For all, faced with the same issue

Add to your proftpd.conf:
```
  <IfModule mod_facts.c>
    FactsAdvertise off
  </IfModule>
```
This will fix Filezilla issues

---

