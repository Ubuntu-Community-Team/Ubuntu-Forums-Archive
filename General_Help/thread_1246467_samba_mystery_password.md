---
title: "samba mystery password"
date: 2009-08-21
forum: General Help
---

### Post by st01k on 2009-08-21
Hi all! I've got a problem here and welcome any suggestions.

Running 8.10 - Intrepid Ibex

Samba was working fine until about two days ago when I updated and I remember seeing some samba updates in the list.  Now, when I try to access my file server from the client computers (several laptops running XP and one running Vista) I get the annoying, "cannot be accessed. Please contact your network admin blah, blah, blah."  

I ran ps -ea | grep smbd and got two samba processes running (checked to make sure 2 of them was ok and all pages says it's a go).  I stopped samba and restarted just to make sure and the same result came back.  Then I went on with the troubleshooting process and tried to mount a samba share locally with: 

mount //localhost/sharename /media/sharename

result:

root@nerve:/media# mount //localhost/obiwan /media/temp
Password: 
mount error 13 = Permission denied
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)

WTF is this password?  I tried my root password and all others for each user but none work.  I don't remember ever setting a 'master' samba password, and if I had it would have been my root password.  I tried just hitting enter with a null field... nada.  And, if it doesn't ask me for a username how does it even know where to look for the associated password?  I'm out of ideas.  Can anyone shed some light?

Side Note: Don't know if this may have anything to do with it, but these are among the last few entries in /var/log/samba/samba.log
==============================================================
[2009/08/20 00:18:17,  1] smbd/service.c:close_cnum(1405)
  xavier (192.168.1.100) closed connection to service cyclops
[2009/08/20 00:18:17,  1] smbd/service.c:close_cnum(1405)
  xavier (192.168.1.100) closed connection to service morpheus
[2009/08/20 00:18:17,  1] smbd/service.c:close_cnum(1405)
  xavier (192.168.1.100) closed connection to service neo
[2009/08/20 00:18:17,  1] smbd/service.c:close_cnum(1405)
  xavier (192.168.1.100) closed connection to service obiwan
[2009/08/20 00:18:17,  1] smbd/service.c:close_cnum(1405)
  xavier (192.168.1.100) closed connection to service seraph
[2009/08/20 00:18:17,  1] smbd/service.c:close_cnum(1405)
  xavier (192.168.1.100) closed connection to service socrates
[2009/08/20 00:18:17,  1] smbd/service.c:close_cnum(1405)
  xavier (192.168.1.100) closed connection to service cerebro
[2009/08/20 00:19:43,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2353)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/08/20 00:24:59,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2353)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/08/20 02:23:03,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2353)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/08/20 20:07:02,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2353)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
[2009/08/20 23:48:45,  0] winbindd/winbindd_cache.c:initialize_winbindd_cache(2353)
  initialize_winbindd_cache: clearing cache and re-creating with version number 1
=====================================================================
The connection closed on each drive is what piqued my interest... is that normal and could it be the cause of my problem?

Here are the contents of my smb.conf:
=======================================
[global]
netbios name = nerve
server string = 
workgroup = GAMEZ
security = user
hosts allow = 127. 192.168.0. 192.168.1.
interfaces = 127.0.0.1/8 192.168.0.0/24 192.168.1.1/15
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
printcap name = /etc/printcap
load printers = yes
cups options = raw
printing = cups
guest account = smbguest
log file = /var/log/samba/samba.log
max log size = 1000
null passwords = no
username level = 8
password level = 8
encrypt passwords = true
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
wins server = 
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

[cyclops]
path = /media/cyclops
comment = music, audiobooks, lectures, etc.
valid users = st01k phoenix
write list = st01k phoenix
admin users = st01k phoenix
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
write list = @users

[jabba]
path = /media/jabba
comment = tv shows, video classes, porn
valid users = st01k phoenix
write list = st01k phoenix
admin users = st01k phoenix
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
write list = @users

[morpheus]
path = /media/morpheus
comment = the red pill
valid users = st01k phoenix
write list = st01k phoenix
admin users = st01k
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
write list = @users

[neo]
path = /media/neo
comment = torrentz
valid users = st01k phoenix
write list = st01k phoenix
admin users = st01k
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
write list = @users

[obiwan]
path = /media/obiwan
comment = software, documents, pictures, video
valid users = st01k phoenix
write list = st01k phoenix
admin users = st01k phoenix
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
write list = @users

[seraph]
path = /media/seraph
comment = movies
valid users = st01k phoenix
write list = st01k phoenix
admin users = st01k phoenix
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
write list = @users

[socrates]
path = /media/socrates
comment = digital library
valid users = st01k phoenix
write list = st01k phoenix
admin users = st01k
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
write list = @users

[webserver]
path = /var/www
comment = apache webserver
valid users = st01k
write list = st01k
admin users = st01k
read only = no
available = yes
browseable = yes
writable = yes
guest ok = no
public = no
printable = no
share modes = no
locking = no
write list = @st01k
==================================================================

Sorry, forgot how to do the nifty text boxes and don't want to look it up right now.  

Thanx!
st01k

---

