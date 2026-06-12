---
title: "Setting up Samba server"
date: 2009-08-20
forum: General Help
---

### Post by mickwombat on 2009-08-20
I'm trying to setup a Samba server and just can't seem to get it to work.
I can see the server from another PC, but can't browse the folders.

When I try to connect from the server, I get

> mick@SLES:~> smbclient //localhost/share/samba/mick -U mick
Enter mick's password: 
Domain=[SLES] OS=[Unix] Server=[Samba 3.2.7-11.7.1-2154-SUSE-CODE11]
tree connect failed: NT_STATUS_BAD_NETWORK_NAME


I've serch on google already and have made the share directories, including parent, globally read/write.

Don't know what to do

Thanks

---

### Post by nerdzero on 2009-08-20
Maybe you are suffering from this bug:  [https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/95452](https://bugs.launchpad.net/ubuntu/+source/kdenetwork/+bug/95452)

If it's in your smb.conf file, try removing the line for the "msdfs proxy" option.

---

### Post by mickwombat on 2009-08-20
Hi,

I did see that somewhere earlier as well, but couldn't see how to remove that line.  I'm using SWAT to configure, but when I edit /etc/samba/smb.conf is only gives me the shortened version and many of the options (that are available when you click advanced in SWAT), just don't seem to appear.

It is driving me absolutely bonkers.....three nights and counting now!!!

Where is the 'full' version of smb.conf kept, or can I change the SWAT program/script to take this out completely.

I have a share configured with exactly the same parameters as, print$, except added a valid user.  I can browse to, print$, no problem, but get this stupid error when I try to browse to the one I have setup.

Not a newbie here, so be as complicated as you like.

Thanks

---

### Post by nerdzero on 2009-08-20
Here's the file you need to take a look at: /etc/samba/smb.conf

It's entirely possible that the line is not there and you are suffering from a different issue.  

If it is there and you remove it, make sure you restart samba after editing smb.conf

Edit:  Nevermind, I read your last post too fast.  The additional values in SWAT are just not written to smb.conf if they are not specified or left at defaults.

---

### Post by nerdzero on 2009-08-20
Maybe post your smb.conf file?

---

### Post by mickwombat on 2009-08-21
Smb.con file below



> [global]
netbios name = UBUNTU-LAPTOP
server string = Samba file and print server
workgroup = Workgroup
security = user
hosts allow = 127. 192.168.
interfaces = 127.0.0.1/8 192.168.2.0/24
bind interfaces only = yes
remote announce = 192.168.2.255
remote browse sync = 192.168.2.255
printcap name = cups
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 6
password level = 6
encrypt passwords = yes
unix password sync = yes
socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
local master = no
domain master = no
preferred master = no
domain logons = no
os level = 33
logon drive = m:
logon home = \\%L\homes\%u
logon path = \\%L\profiles\%u
logon script = %G.bat
time server = no
name resolve order = wins lmhosts bcast
wins support = no
wins proxy = no
dns proxy = no
preserve case = yes
short preserve case = yes
client use spnego = no
client signing = no
client schannel = no
server signing = no
server schannel = no
nt pipe support = yes
nt status support = yes
allow trusted domains = no
obey pam restrictions = yes
enable spoolss = yes
client plaintext auth = no
disable netbios = no
follow symlinks = no
update encrypted = yes
pam password change = no
passwd chat timeout = 120
hostname lookups = no
username map = /etc/samba/smbusers
smb passwd file = /etc/samba/smbpasswd
passwd program = /usr/bin/passwd '%u'
passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
add group script = /usr/sbin/groupadd '%g'
delete user script = /usr/sbin/userdel '%u'
delete user from group script = /usr/sbin/userdel '%u' '%g'
delete group script = /usr/sbin/groupdel '%g'
add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
machine password timeout = 120
idmap uid = 16777216-33554431
idmap gid = 16777216-33554431
template shell = /dev/null
winbind use default domain = yes
winbind separator = @
winbind cache time = 360
winbind trusted domains only = yes
winbind nested groups = no
winbind nss info = no
winbind refresh tickets = no
winbind offline logon = no

[homes]
comment = Home Directories
path = /home
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no

[netlogon]
comment = Network Logon Service
path = /home/netlogon
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

[profiles]
comment = User Profiles
path = /var/samba/profiles
read only = no
available = yes
browseable = no
writable = yes
guest ok = no
public = no
printable = no
locking = no
create mode = 0600
directory mask = 0700

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
share modes = no
locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes

[pdf-printer]
path = /tmp
comment = PDF Printer Service
printable = yes
guest ok = yes
use client driver = yes
printing = bsd
print command = /usr/bin/gadmin-samba-pdf %s %u
lpq command =
lprm command =

[mick]
path = /share/samba/mick
comment = No comment
valid users = ubuntu
write list = ubuntu
read only = no
available = yes
browseable = yes
writable = no
guest ok = no
public = no
printable = no
share modes = no
locking = no

Cheers

---

### Post by nerdzero on 2009-08-21
Let's start with only a couple shares at first.  How does this work?   You can add the other entries and options back in when you get these working.

If this doesn't work, try restoring the smb.conf file that is installed by default, confirming it works, and then editing it by hand.  Maybe SWAT is putting something in there it doesn't like.

```
[global]
netbios name = UBUNTU-LAPTOP
server string = Samba file and print server
workgroup = Workgroup
domain master = yes
local master = yes
preferred master = yes
os level = 255
wins support = yes
dns proxy = no
log file = /var/log/samba/samba.log
max log size = 1000
syslog = 0
encrypt passwords = true
passdb backend = tdbsam
obey pam restrictions = yes
unix password sync = yes
passwd program = /usr/bin/passwd %u
passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
pam password change = yes
map to guest = bad user
socket options = TCP_NODELAY IPTOS_LOWDELAY
getwd cache = yes
dead time = 15

[homes]
comment = Home Directories
path = /home

[mick]
path = /share/samba/mick
comment = No comment
```

---

