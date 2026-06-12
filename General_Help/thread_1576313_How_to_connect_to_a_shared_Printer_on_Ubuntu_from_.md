---
title: "How to connect to a shared Printer on Ubuntu from a Windows machine ?"
date: 2010-09-17
forum: General Help
---

### Post by eXtremer on 2010-09-17
Hi all.
I've successfully installed a printer on Ubuntu, then I shared this printer but I can't find it on the network, what is the default sharename ? In Windows I create a local port then I show the printer network path for ex.: \\192.168.0.193\PrinterName, When I try to do it in my case \\192.168.0.193\Canon\MF4100%20Series it doesn't work.

Here is a screenshot:

[[IMG]http://img251.imageshack.us/img251/8022/screenshotud.th.png[/IMG]]("http://img251.imageshack.us/img251/8022/screenshotud.png")

I would really appreciate any help, thank you in advance.

---

### Post by sikander3786 on 2010-09-17
Did you try navigating to

http://<hostname>:631/printers/<printername>

from a browser on Windows? Can it browse the printer?

Also under policies menu, make sure Shared and Browseable or something like that (I can't remember the exact wording) is ticked in the Printing Menu on Ubuntu.

Also seen this link.

[https://help.ubuntu.com/community/NetworkPrintingFromWinXP](https://help.ubuntu.com/community/NetworkPrintingFromWinXP)

---

### Post by jodlajodla on 2010-09-17
Have you done [this]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP")? If you have firewall then you need to open some ports. I recommend you to change name of printer to printer or something else, for faster and easier connect to it.

---

### Post by eXtremer on 2010-09-17
> **jodlajodla said:**
> Have you done [this]("https://help.ubuntu.com/community/NetworkPrintingFromWinXP")? If you have firewall then you need to open some ports. I recommend you to change name of printer to printer or something else, for faster and easier connect to it.

I don't know if I have a firewall, does Ubuntu have an enabled firewall ? I've just installed the OS nothing else, btw how can I change the printer name ? In the description Tab ?

---

### Post by eXtremer on 2010-09-18
The issue has been solved, I had to:

1. Install Samba
2. Disable Firewall

Everything works fine now :)

---

### Post by jodlajodla on 2010-09-18
Good ;) I just enabled port on firewall and then works ;) Have fun! :)

---

### Post by eXtremer on 2010-09-21
> **jodlajodla said:**
> Good ;) I just enabled port on firewall and then works ;) Have fun! :)


Unfortunately after I restart the machine the printer works only locally but not on the network (shared) and I know that the problem is in Samba, because when I go to the Samba settings and I untick the "Visible" and "Users who have access" then tick it back it works again - I see the printer on LAN and I cant print but why it happens like this ?  I know it's very easy just to tick it and untick those options but I'm not allways in office and users may have problems, how can I solve this issue with Samba ?

Thank you in advance

---

### Post by eXtremer on 2010-09-21
btw, install distro:

DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.1 LTS"

---

### Post by Morbius1 on 2010-09-21
The problem may not be samba but when cups is starting. The next time you boot start cups and samba in the correct order to determine if that's the problem:

```
sudo service cups restart
```
```
sudo service smbd restart
```

If that resolves the problem there is a permanent workaround for that.

---

### Post by eXtremer on 2010-09-21
> **Morbius1 said:**
> The problem may not be samba but when cups is starting. The next time you boot start cups and samba in the correct order to determine if that's the problem:

```
sudo service cups restart
``````
sudo service smbd restart
```If that resolves the problem there is a permanent workaround for that.

Yes Morbius1 I think this is the issue, here is a screenshot of the commands:

[img]http://img827.imageshack.us/img827/7889/printer.jpg[/img]

...after this the printer is working again.

So, what it the workaround ?

---

### Post by Morbius1 on 2010-09-21
There's a bug report in launchpad that has this workaround ( 494141 ) : 

Edit /etc/init/smbd.conf as root:
```
gksu gedit /etc/init/smbd.conf
```Then change one line:
> description "SMB/CIFS File Server"
author "Steve Langasek <steve.langasek@ubuntu.com>"

[COLOR=Blue]start on local-filesystems[/COLOR]
stop on runlevel [!2345]

respawn

pre-start script
RUN_MODE="daemons"

[ -r /etc/default/samba ] && . /etc/default/samba

[ "$RUN_MODE" = inetd ] && { stop; exit 0; }

install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -FTo this:
> description "SMB/CIFS File Server"
author "Steve Langasek <steve.langasek@ubuntu.com>"

[COLOR=Blue]start on (local-filesystems and stopped rc)[/COLOR]
stop on runlevel [!2345]

respawn

pre-start script
RUN_MODE="daemons"

[ -r /etc/default/samba ] && . /etc/default/samba

[ "$RUN_MODE" = inetd ] && { stop; exit 0; }

install -o root -g root -m 755 -d /var/run/samba
end script

exec smbd -F Cups needs to start first to create the printer list that samba publishes to the network. If samba starts first then there is no list and as far as Samba is concerned there are no printers.

---

### Post by eXtremer on 2010-09-21
It works like a charm, I really appreciate Morbius1, thank you ;)
I think this issue is really solved now :)

---

### Post by eXtremer on 2010-09-23
I don't understand why but sometimes it's working sometimes not, I thin Samba service is not starting or I don't know, today I've installed GADMIN-SAMBA 0.2.8 it has more options for sharing and it is easier to change settings, when I started GADMIN the smb.conf was changed to GADMIN one. Now when I want to see the status of Samba I receive this:

```
nataly@Natalia:~$ sudo samba start
Unknown parameter encountered: "remote announce"
Ignoring unknown parameter "remote announce"
Unknown parameter encountered: "remote browse sync"
Ignoring unknown parameter "remote browse sync"
Unknown parameter encountered: "printcap name"
Ignoring unknown parameter "printcap name"
Unknown parameter encountered: "load printers"
Ignoring unknown parameter "load printers"
Unknown parameter encountered: "cups options"
Ignoring unknown parameter "cups options"
Unknown parameter encountered: "printing"
Ignoring unknown parameter "printing"
Unknown parameter encountered: "guest account"
Ignoring unknown parameter "guest account"
Unknown parameter encountered: "max log size"
Ignoring unknown parameter "max log size"
Unknown parameter encountered: "username level"
Ignoring unknown parameter "username level"
Unknown parameter encountered: "unix password sync"
Ignoring unknown parameter "unix password sync"
Unknown parameter encountered: "domain master"
Ignoring unknown parameter "domain master"
Unknown parameter encountered: "domain logons"
Ignoring unknown parameter "domain logons"
Unknown parameter encountered: "os level"
Ignoring unknown parameter "os level"
Unknown parameter encountered: "logon drive"
Ignoring unknown parameter "logon drive"
Unknown parameter encountered: "logon home"
Ignoring unknown parameter "logon home"
Unknown parameter encountered: "logon path"
Ignoring unknown parameter "logon path"
Unknown parameter encountered: "logon script"
Ignoring unknown parameter "logon script"
Unknown parameter encountered: "wins proxy"
Ignoring unknown parameter "wins proxy"
Unknown parameter encountered: "preserve case"
Ignoring unknown parameter "preserve case"
Unknown parameter encountered: "short preserve case"
Ignoring unknown parameter "short preserve case"
Unknown parameter encountered: "client use spnego"
Ignoring unknown parameter "client use spnego"
Unknown parameter encountered: "client schannel"
Ignoring unknown parameter "client schannel"
Unknown parameter encountered: "server schannel"
Ignoring unknown parameter "server schannel"
Unknown parameter encountered: "nt pipe support"
Ignoring unknown parameter "nt pipe support"
Unknown parameter encountered: "allow trusted domains"
Ignoring unknown parameter "allow trusted domains"
Unknown parameter encountered: "enable spoolss"
Ignoring unknown parameter "enable spoolss"
Unknown parameter encountered: "follow symlinks"
Ignoring unknown parameter "follow symlinks"
Unknown parameter encountered: "update encrypted"
Ignoring unknown parameter "update encrypted"
Unknown parameter encountered: "pam password change"
Ignoring unknown parameter "pam password change"
Unknown parameter encountered: "passwd chat timeout"
Ignoring unknown parameter "passwd chat timeout"
Unknown parameter encountered: "hostname lookups"
Ignoring unknown parameter "hostname lookups"
Unknown parameter encountered: "username map"
Ignoring unknown parameter "username map"
Unknown parameter encountered: "smb passwd file"
Ignoring unknown parameter "smb passwd file"
Unknown parameter encountered: "passwd program"
Ignoring unknown parameter "passwd program"
Unknown parameter encountered: "add user script"
Ignoring unknown parameter "add user script"
Unknown parameter encountered: "add user to group script"
Ignoring unknown parameter "add user to group script"
Unknown parameter encountered: "add group script"
Ignoring unknown parameter "add group script"
Unknown parameter encountered: "delete user script"
Ignoring unknown parameter "delete user script"
Unknown parameter encountered: "delete user from group script"
Ignoring unknown parameter "delete user from group script"
Unknown parameter encountered: "delete group script"
Ignoring unknown parameter "delete group script"
Unknown parameter encountered: "add machine script"
Ignoring unknown parameter "add machine script"
Unknown parameter encountered: "machine password timeout"
Ignoring unknown parameter "machine password timeout"
Unknown parameter encountered: "idmap uid"
Ignoring unknown parameter "idmap uid"
Unknown parameter encountered: "idmap gid"
Ignoring unknown parameter "idmap gid"
Unknown parameter encountered: "winbind use default domain"
Ignoring unknown parameter "winbind use default domain"
Unknown parameter encountered: "winbind cache time"
Ignoring unknown parameter "winbind cache time"
Unknown parameter encountered: "winbind trusted domains only"
Ignoring unknown parameter "winbind trusted domains only"
Unknown parameter encountered: "winbind nested groups"
Ignoring unknown parameter "winbind nested groups"
Unknown parameter encountered: "winbind nss info"
Ignoring unknown parameter "winbind nss info"
Unknown parameter encountered: "winbind refresh tickets"
Ignoring unknown parameter "winbind refresh tickets"
Unknown parameter encountered: "winbind offline logon"
Ignoring unknown parameter "winbind offline logon"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "create mode"
Ignoring unknown parameter "create mode"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "writable"
Ignoring unknown parameter "writable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "public"
Ignoring unknown parameter "public"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "writeable"
Ignoring unknown parameter "writeable"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "locking"
Ignoring unknown parameter "locking"
Unknown parameter encountered: "guest ok"
Ignoring unknown parameter "guest ok"
Unknown parameter encountered: "use client driver"
Ignoring unknown parameter "use client driver"
Unknown parameter encountered: "printing"
Ignoring unknown parameter "printing"
Unknown parameter encountered: "print command"
Ignoring unknown parameter "print command"
Unknown parameter encountered: "lpq command"
Ignoring unknown parameter "lpq command"
Unknown parameter encountered: "lprm command"
Ignoring unknown parameter "lprm command"
@Natalia:~$ ~

```Here is my smb.conf

```
[global]
netbios name = Samba24
server string = Samba file and print server
workgroup = Workgroup
security = user
hosts allow = 127. 192.168.0.
interfaces = 127.0.0.1/8 192.168.0.0/24
bind interfaces only = yes
remote announce = 192.168.0.255
remote browse sync = 192.168.0.255
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
add user to group script=/usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
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
locking = no
strict locking = no

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
locking = no
strict locking = no

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
create mode = 0600
directory mask = 0700
locking = no
strict locking = no

[printers]
comment = All Printers
path = /var/spool/samba
browseable = yes
writable = no
guest ok = no
public = no
printable = yes
locking = no
strict locking = no

[pdf-documents]
path = /home/pdf-documents
comment = Converted PDF Documents
available = yes
browseable = yes
writeable = yes
guest ok = yes
locking = no
strict locking = no

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

```[[IMG]http://img841.imageshack.us/img841/8715/gadmin.th.png[/IMG]]("http://img841.imageshack.us/img841/8715/gadmin.png")


What to do, I really need my prrinter sharing to work normally.
Thank you, any help really appreciated.

---

### Post by Morbius1 on 2010-09-23
GADMIN-SAMBA was designed specifically for the network administrator that is degree bearing, has over 22 years of practical experience in Samba and has full mastery over the more obscure and arcane parameters available in Samba. It was never intended to be used by mortals. As I am a mere mortal I can't help you get out of this but I do have a recommendation - start over with a fresh smb.conf.

Reinstalling Samba won't reset smb.conf so you have two choices:

(1) See if GADMIN-SAMBA had the decency of creating a backup of your original smb.conf and try to restore it and unistall gadmin so this won't happen again.

(2) There is an emergency backup of smb.conf for people like you and I that can be used for situations like this:

**(1) Make sure the following file exists: **
/usr/share/samba/smb.conf

**(2) Make another backup of your current smb.conf**
```
sudo cp /etc/samba/smb.conf /etc/samba/smb.confMOD 
```**(3) Start with a fresh one:**
```
sudo cp -a /usr/share/samba/smb.conf /etc/samba/ 
```**(4) Correct one mistake in the new one:**
Find the line:
> encrypt passwords = falseand change it to:
> encrypt passwords = true**(5) Restart samba**
```
sudo service smbd restart
```

---

### Post by eXtremer on 2010-09-23
1. I've removed GADMIN
2. I've reinstalled samba like this:
sudo apt-get remove samba samba-common --purge
then
sudo apt-get install samba system-config-samba

3. Look what happens when I try to start samba:
nataly@Natalia:~$ sudo service smbd start
smbd start/running, process 2636
nataly@Natalia:~$ sudo service smbd status
smbd stop/waiting
nataly@Natalia:~$

It says that samba started but when I do status, it is stopped, yes ? why ?

Here is a full log off smbd.log
```

[2010/09/23 16:42:40,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:40,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x9e862d]
   #1 smbd(+0x615383) [0xcce383]
   #2 smbd(+0x6155c3) [0xcce5c3]
   #3 smbd(main+0xa91) [0xccf561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x3e1bd6]
   #5 smbd(+0x8b231) [0x744231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x7d962d]
   #1 smbd(+0x615383) [0xabf383]
   #2 smbd(+0x6155c3) [0xabf5c3]
   #3 smbd(main+0xa91) [0xac0561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xd45bd6]
   #5 smbd(+0x8b231) [0x535231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xa2762d]
   #1 smbd(+0x615383) [0xd0d383]
   #2 smbd(+0x6155c3) [0xd0d5c3]
   #3 smbd(main+0xa91) [0xd0e561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xe84bd6]
   #5 smbd(+0x8b231) [0x783231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x70f62d]
   #1 smbd(+0x615383) [0x9f5383]
   #2 smbd(+0x6155c3) [0x9f55c3]
   #3 smbd(main+0xa91) [0x9f6561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xb6cbd6]
   #5 smbd(+0x8b231) [0x46b231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xab362d]
   #1 smbd(+0x615383) [0xd99383]
   #2 smbd(+0x6155c3) [0xd995c3]
   #3 smbd(main+0xa91) [0xd9a561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xfbebd6]
   #5 smbd(+0x8b231) [0x80f231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x9de62d]
   #1 smbd(+0x615383) [0xcc4383]
   #2 smbd(+0x6155c3) [0xcc45c3]
   #3 smbd(main+0xa91) [0xcc5561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xfcebd6]
   #5 smbd(+0x8b231) [0x73a231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb1b62d]
   #1 smbd(+0x615383) [0xe01383]
   #2 smbd(+0x6155c3) [0xe015c3]
   #3 smbd(main+0xa91) [0xe02561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x3dcbd6]
   #5 smbd(+0x8b231) [0x877231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xadf62d]
   #1 smbd(+0x615383) [0xdc5383]
   #2 smbd(+0x6155c3) [0xdc55c3]
   #3 smbd(main+0xa91) [0xdc6561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x46abd6]
   #5 smbd(+0x8b231) [0x83b231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x84b62d]
   #1 smbd(+0x615383) [0xb31383]
   #2 smbd(+0x6155c3) [0xb315c3]
   #3 smbd(main+0xa91) [0xb32561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xf3ebd6]
   #5 smbd(+0x8b231) [0x5a7231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x74862d]
   #1 smbd(+0x615383) [0xa2e383]
   #2 smbd(+0x6155c3) [0xa2e5c3]
   #3 smbd(main+0xa91) [0xa2f561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xf8fbd6]
   #5 smbd(+0x8b231) [0x4a4231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:42:44,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:42:44,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:42:44,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:42:44,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:42:44,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:42:44,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x6a962d]
   #1 smbd(+0x615383) [0x98f383]
   #2 smbd(+0x6155c3) [0x98f5c3]
   #3 smbd(main+0xa91) [0x990561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xba1bd6]
   #5 smbd(+0x8b231) [0x405231]
[2010/09/23 16:42:44,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:23,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:23,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:23,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:23,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x68562d]
   #1 smbd(+0x615383) [0x96b383]
   #2 smbd(+0x6155c3) [0x96b5c3]
   #3 smbd(main+0xa91) [0x96c561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xb94bd6]
   #5 smbd(+0x8b231) [0x3e1231]
[2010/09/23 16:51:23,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:23,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:23,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:23,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:23,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xabc62d]
   #1 smbd(+0x615383) [0xda2383]
   #2 smbd(+0x6155c3) [0xda25c3]
   #3 smbd(main+0xa91) [0xda3561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x42ebd6]
   #5 smbd(+0x8b231) [0x818231]
[2010/09/23 16:51:23,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:23,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:23,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:23,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:23,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x80962d]
   #1 smbd(+0x615383) [0xaef383]
   #2 smbd(+0x6155c3) [0xaef5c3]
   #3 smbd(main+0xa91) [0xaf0561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xfa2bd6]
   #5 smbd(+0x8b231) [0x565231]
[2010/09/23 16:51:23,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:23,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:23,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:23,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:23,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb7a62d]
   #1 smbd(+0x615383) [0xe60383]
   #2 smbd(+0x6155c3) [0xe605c3]
   #3 smbd(main+0xa91) [0xe61561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x646bd6]
   #5 smbd(+0x8b231) [0x8d6231]
[2010/09/23 16:51:23,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:23,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:23,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:23,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:23,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb9e62d]
   #1 smbd(+0x615383) [0xe84383]
   #2 smbd(+0x6155c3) [0xe845c3]
   #3 smbd(main+0xa91) [0xe85561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xffbbd6]
   #5 smbd(+0x8b231) [0x8fa231]
[2010/09/23 16:51:23,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:23,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:23,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:23,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:23,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:23,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:23,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xbab62d]
   #1 smbd(+0x615383) [0xe91383]
   #2 smbd(+0x6155c3) [0xe915c3]
   #3 smbd(main+0xa91) [0xe92561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x1008bd6]
   #5 smbd(+0x8b231) [0x907231]
[2010/09/23 16:51:23,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:24,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:24,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:24,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:24,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x60f62d]
   #1 smbd(+0x615383) [0x8f5383]
   #2 smbd(+0x6155c3) [0x8f55c3]
   #3 smbd(main+0xa91) [0x8f6561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xf17bd6]
   #5 smbd(+0x8b231) [0x36b231]
[2010/09/23 16:51:24,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:24,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:24,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:24,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:24,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xb8e62d]
   #1 smbd(+0x615383) [0xe74383]
   #2 smbd(+0x6155c3) [0xe745c3]
   #3 smbd(main+0xa91) [0xe75561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x65abd6]
   #5 smbd(+0x8b231) [0x8ea231]
[2010/09/23 16:51:24,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:24,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:24,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:24,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:24,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x8cd62d]
   #1 smbd(+0x615383) [0xbb3383]
   #2 smbd(+0x6155c3) [0xbb35c3]
   #3 smbd(main+0xa91) [0xbb4561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xe04bd6]
   #5 smbd(+0x8b231) [0x629231]
[2010/09/23 16:51:24,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:24,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:24,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:24,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:24,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0x5b862d]
   #1 smbd(+0x615383) [0x89e383]
   #2 smbd(+0x6155c3) [0x89e5c3]
   #3 smbd(main+0xa91) [0x89f561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0xf7cbd6]
   #5 smbd(+0x8b231) [0x314231]
[2010/09/23 16:51:24,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd
[2010/09/23 16:51:24,  0] smbd/server.c:1069(main)
  smbd version 3.4.7 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2010/09/23 16:51:24,  0] smbd/server.c:1115(main)
  standard input is not a socket, assuming -D option
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 445 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] lib/util_sock.c:938(open_socket_in)
  bind failed on port 139 socket_addr = 0.0.0.0.
  Error = Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:457(smbd_open_one_socket)
  smbd_open_once_socket: open_socket_in: Address already in use
[2010/09/23 16:51:24,  0] smbd/server.c:616(open_sockets_smbd)
  open_sockets_smbd: No sockets available to bind to.
[2010/09/23 16:51:24,  0] smbd/server.c:837(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] smbd/server.c:839(exit_server_common)
  Abnormal server exit: open_sockets_smbd() failed
[2010/09/23 16:51:24,  0] smbd/server.c:840(exit_server_common)
  ===============================================================
[2010/09/23 16:51:24,  0] lib/util.c:1584(log_stack_trace)
  BACKTRACE: 6 stack frames:
   #0 smbd(log_stack_trace+0x2d) [0xbcc62d]
   #1 smbd(+0x615383) [0xeb2383]
   #2 smbd(+0x6155c3) [0xeb25c3]
   #3 smbd(main+0xa91) [0xeb3561]
   #4 /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x17b4bd6]
   #5 smbd(+0x8b231) [0x928231]
[2010/09/23 16:51:24,  0] lib/fault.c:326(dump_core)
  dumping core in /var/log/samba/cores/smbd

```What's wrong again ? I'm not a frequent user of Linux (I am now) sorry if I give to many stupid questions, thank you in advance.

---

### Post by Morbius1 on 2010-09-23
I hope you don't mind me saying this but you seem to have a tendency to go to extremes. There was no need to purge your system of all things samba. All you needed to do was restore smb.conf to it's original state.

I really have no idea what the problem is with your system at this point but make sure you have the following packages installed:
```
libsmbclient
nautilus-share
samba
samba-common
samba-common-bin
smbclient
```Then restore the original smb.conf as I described in the 5-step process in my earlier post.

Then reboot

Once you're back up find out if the following services are started:
```
sudo service cups status
sudo service smbd status
sudo service nmbd status
```Finally post the output of the following command:
```
 testparm -s
```

---

