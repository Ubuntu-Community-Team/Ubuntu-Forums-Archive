---
title: "Samba/Webmin Screwup on Ubuntu Server"
date: 2011-06-15
forum: General Help
---

### Post by poetech on 2011-06-15
So I inherited an environment with about 40 or so machines, all windows, with 5 servers, 2 windows and 3 ubuntu server. Two of the ubuntu servers are running samba and serve as domain controllers for the environment. I installed webmin on all of the ubuntu servers to better manage the servers and get a better understanding of what's going on with them. I screwed up when I was trying to create a new user and used the 'convert unix users to samba users' button in the samba module and now for some reason the domain is unavailable and folks can't write to shares. The log for what the conversion did shows that it added 39 machine users to samba. I've tried deleting them to no avail but in doing that I also noticed that the samba user list was much shorter than what I'd originally seen, so I'm not sure if it just modified them and if so what it did.

Anyone familiar with a situation like this?

---

### Post by poetech on 2011-06-15
Here's the samba config I'm using if this is helpful to solving the issue:


[global]
workgroup = JUKEJOINT
netbios name = GENERALSRV
server string = %h
os level = 255
security = user
domain logons = yes
local master = yes
domain master = yes
preferred master = yes
enable privileges = yes
passdb backend = tdbsam
encrypt passwords = true
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *New*password* %n\n *Retype*new*password* %n\n *passwd:*all*authentication*t                                                                              okens*updated*successfully*
pam password change = yes
obey pam restrictions = yes
add user script = /usr/sbin/useradd -m %u
delete user script = /usr/sbin/userdel -r %u
add group script = /usr/sbin/groupadd %g
delete group script = /usr/sbin/groupdel %g
add user to group script = /usr/sbin/groupmod -A %u %g
delete user from group script = /usr/sbin/groupmod -R %u %g
add machine script = /usr/sbin/useradd -s /bin/false -d /var/lib/nobody %u
# Note: The following specifies the default logon script.
# Per user logon scripts can be specified in the user account using pdbedit
logon script = logon.cmd
# This sets the default profile path. Set per user paths with pdbedit

# Enable roaming profiles
#logon path = \\%L\profiles\%U
#logon drive = P:
#logon home = \\%L\%U
# End romaing profiles settings

idmap uid = 10000-20000
idmap gid = 10000-20000
winbind enum groups = yes
winbind enum users = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
# hosts allow = 192.168.1. localhost
wins support = yes
name resolve order = wins lmhosts hosts bcast
dns proxy = no
remote announce = 192.168.1.255
log file = /var/log/samba/log.%m
max log size = 1000
log level = 1
panic action = /usr/share/samba/panic-action %d
load printers = no
dos charset = UTF-8
unix charset = UTF8
display charset = UTF8
preserve case = yes
case sensitive = no
map to guest = Bad User

# Un-comment the following and create the netlogon directory for Domain Logons
# (you need to configure Samba to act as a domain controller too.)
[netlogon]
   comment = Network Logon Service
   path = /home/samba/netlogon
   guest ok = yes
   read only = yes
   browsable = no
   share modes = no

# Un-comment the following and create the profiles directory to store
# users profiles (see the "logon path" option above)
# (you need to configure Samba to act as a domain controller too.)
# The path below should be writable by all users so that their
# profile directory may be created the first time they log on
[profiles]
   comment = Network Profiles Share
   path = /home/samba/profiles
   read only = no
   store dos attributes = yes
   guest ok = no
   browseable = no
   printable = no
   create mask = 0600
   directory mask = 0700
   hide files = /desktop.ini/outlook*.lnk/Briefcase*/
   oplocks = false
   level2 oplocks = false

---

