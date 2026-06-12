---
title: "PROFTPD Issues"
date: 2009-09-18
forum: General Help
---

### Post by mistaWAC on 2009-09-18
So I'm having an issue with Proftpd.  I apt-got it and it installed fine.  I changed it's file directory from home to /media/sda3/server under 644 permissions and when I try to log in it's telling me I'm giving it the wrong password.  Any help?

Thanks

---

### Post by Dantheman53 on 2009-09-18
Its hard to tell what the problem would be without a little more information.

Can you post your proftpd.conf

/etc/proftpd/proftpd.conf

---

### Post by mistaWAC on 2009-09-18
Here ya go:

To note:
[LIST]
[*]Running Ubuntu Server 9.04
[*]Ports are forwarded correctly
[*]No users can log in with normal log in information
[*]Moved file directory to /media/sda3/server with 644 permissions set and root as owner
[/LIST]


#
# /etc/proftpd/proftpd.conf -- This is a basic ProFTPD configuration file.
# To really apply changes reload proftpd after modifications.
# 

# Includes DSO modules
Include /etc/proftpd/modules.conf

# Set off to disable IPv6 support which is annoying on IPv4 only boxes.
UseIPv6				off
# If set on you can experience a longer connection delay in many cases.
IdentLookups			off

ServerName			"WACserver"
ServerType			standalone
DeferWelcome			off

MultilineRFC2228		on
DefaultServer			on
ShowSymlinks			on

TimeoutNoTransfer		600
TimeoutStalled			600
TimeoutIdle			1200

DisplayLogin                    welcome.msg
DisplayChdir               	.message true
ListOptions                	"-l"

DenyFilter			\*.*/

# Use this to jail all users in their homes 
DefaultRoot			/media/sda3/server/

# Users require a valid shell listed in /etc/shells to login.
# Use this directive to release that constrain.
# RequireValidShell		off

# Port 21 is the standard FTP port.
Port				21

# In some cases you have to specify passive ports range to by-pass
# firewall limitations. Ephemeral ports can be used for that, but
# feel free to use a more narrow range.
# PassivePorts                  49152 65534

# If your host was NATted, this option is useful in order to
# allow passive tranfers to work. You have to use your public
# address and opening the passive ports used on your firewall as well.
# MasqueradeAddress		1.2.3.4

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
MaxInstances			30

# Set the user and group that the server normally runs at.
User				nobody
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
SystemLog   /var/log/proftpd/proftpd.log

<IfModule mod_quotatab.c>
QuotaEngine off
</IfModule>

<IfModule mod_ratio.c>
Ratios off
</IfModule>


# Delay engine reduces impact of the so-called Timing Attack described in
# [http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02](http://security.lss.hr/index.php?page=details&ID=LSS-2004-10-02)
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

# A basic anonymous configuration, no upload directories.

# <Anonymous ~ftp>
#   User				ftp
#   Group				nogroup
#   # We want clients to be able to login with "anonymous" as well as "ftp"
#   UserAlias			anonymous ftp
#   # Cosmetic changes, all files belongs to ftp user
#   DirFakeUser	on ftp
#   DirFakeGroup on ftp
# 
#   RequireValidShell		off
# 
#   # Limit the maximum number of anonymous logins
#   MaxClients			10
# 
#   # We want 'welcome.msg' displayed at login, and '.message' displayed
#   # in each newly chdired directory.
#   DisplayLogin			welcome.msg
#   DisplayChdir		.message
# 
#   # Limit WRITE everywhere in the anonymous chroot
#   <Directory *>
#     <Limit WRITE>
#       DenyAll
#     </Limit>
#   </Directory>
# 
#   # Uncomment this if you're brave.
#   # <Directory incoming>
#   #   # Umask 022 is a good standard umask to prevent new files and dirs
#   #   # (second parm) from being group and world writable.
#   #   Umask				022  022
#   #            <Limit READ WRITE>
#   #            DenyAll
#   #            </Limit>
#   #            <Limit STOR>
#   #            AllowAll
#   #            </Limit>
#   # </Directory>
# 
# </Anonymous>

---

### Post by Dantheman53 on 2009-09-18
Lets see if this helps you out.... 

Make sure you make a backup of proftpd.conf before you change it!

1. You'll have to uncomment this line if you're behind a router:
> 
PassivePorts                  49152 65534
then make sure those are fowarded on the router

2. If your behind a router you'll have to uncomment and put in your ip
> 
MasqueradeAddress 123.456.789.123
3. At the bottom of the file you'll have to tell what directory to use.

For example this is what i have to get mine to work
> 
<Directory /home/ftp>
Umask 022 022
AllowStoreRestart on
AllowOverwrite on
        <Limit RMD>
        DenyAll
        </Limit>

        <Limit STOR OWD MKD>
        AllowAll
        </Limit>
</Directory>
Change the first line so it points to /media/sda3/server

4. Also if you want to restrict certain users you can add this
> 
<Limit LOGIN>
AllowUser ftpuser
DenyALL
</Limit>


After you have made the changes make sure you restart proftpd

> sudo /etc/init.d/proftpd restart


These are the things i did to get mine to work, but i'm no expert....

---

### Post by mistaWAC on 2009-09-18
Bah, didn't work.

---

### Post by Dantheman53 on 2009-09-18
Damn

Ok try this just to see if we can get it to work

> sudo chmod 777 /media/sda3/server And

In proftpd.conf uncomment 

> RequireValidShell        off

Also restart proftpd

> sudo /etc/init.d/proftpd restart

---

