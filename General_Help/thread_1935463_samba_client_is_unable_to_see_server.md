---
title: "samba client is unable to see server"
date: 2012-03-04
forum: General Help
---

### Post by jessel on 2012-03-04
I have a desktop running Ubuntu 10.04 with a shared folder and a shared printer.

I can access the shared folder and the shared printer from my mac laptop, but not from my wifes asus x101 netbook that runs ubuntu 11.10.

when I try to find network printer a popup comes up:
There were no print shares found.  Please check that the Samba service is marked as trusted in your firewall configuration.

i shut off the firwall, but still got the same error as above
molly@x101:~$ sudo ufw status
[sudo] password for molly: 
Status: inactive

when i try to look at the shared samba folder in the file browser:
Error: DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
Please select another viewer and try again.

here's samba specific configuration info
molly@x101:~$ testparm -s
```
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Processing section "[homes]"
Processing section "[netlogon]"
Processing section "[profiles]"
Processing section "[printers]"
Processing section "[pdf-documents]"
Processing section "[pdf-printer]"
Loaded services file OK.
WARNING: You have some share names that are longer than 12 characters.
These may not be accessible to some older clients.
(Eg. Windows9x, WindowsMe, and smbclient prior to Samba 3.0.)
Server role: ROLE_STANDALONE
[global]
    netbios name = LORIS
    server string = Samba file and print server
    interfaces = 127.0.0.1/8, 192.168.0.0/24
    bind interfaces only = Yes
    update encrypted = Yes
    client schannel = No
    server schannel = No
    allow trusted domains = No
    obey pam restrictions = Yes
    guest account = smbguest
    passwd program = /usr/bin/passwd '%u'
    passwd chat = *New*password* %n\n *ReType*new*password* %n\n *passwd*changed*\n
    passwd chat timeout = 120
    username map = /etc/samba/smbusers
    password level = 6
    username level = 6
    unix password sync = Yes
    log file = /var/log/samba/samba.log
    max log size = 1000
    name resolve order = bcast host
    client signing = No
    client use spnego = No
    socket options = TCP_NODELAY SO_RCVBUF=8192 SO_SNDBUF=8192
    printcap name = cups
    machine password timeout = 120
    add user script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null '%u'
    delete user script = /usr/sbin/userdel '%u'
    add group script = /usr/sbin/groupadd '%g'
    delete group script = /usr/sbin/groupdel '%g'
    add user to group script = /usr/sbin/useradd -d /dev/null -c 'Samba User Account' -s /dev/null -g '%g' '%u'
    delete user from group script = /usr/sbin/userdel '%u' '%g'
    add machine script = /usr/sbin/useradd -d /dev/null -g sambamachines -c 'Samba Machine Account' -s /dev/null -M '%u'
    logon script = %G.bat
    logon path = \\%L\profiles\%u
    logon drive = m:
    logon home = \\%L\homes\%u
    os level = 33
    local master = No
    domain master = No
    dns proxy = No
    remote announce = 192.168.0.255
    remote browse sync = 192.168.0.255
    idmap uid = 16777216-33554431
    idmap gid = 16777216-33554431
    template shell = /dev/null
    winbind separator = @
    winbind cache time = 360
    winbind use default domain = Yes
    winbind trusted domains only = Yes
    winbind nested groups = No
    winbind nss info = no
    hosts allow = 127., 192.168.0.
    cups options = raw
    follow symlinks = No

[homes]
    comment = Home Directories
    path = /home
    read only = No
    locking = No
    strict locking = No

[netlogon]
    comment = Network Logon Service
    path = /home/netlogon
    locking = No
    strict locking = No

[profiles]
    comment = User Profiles
    path = /var/samba/profiles
    read only = No
    create mask = 0600
    directory mask = 0700
    browseable = No
    locking = No
    strict locking = No

[printers]
    comment = All Printers
    path = /var/spool/samba
    printable = Yes
    browseable = No
    locking = No
    strict locking = No

[pdf-documents]
    comment = Converted PDF Documents
    path = /home/pdf-documents
    read only = No
    guest ok = Yes
    locking = No
    strict locking = No

[pdf-printer]
    comment = PDF Printer Service
    path = /tmp
    guest ok = Yes
    printable = Yes
    printing = bsd
    print command = /usr/bin/gadmin-samba-pdf %s %u
    lpq command = 
    use client driver = Yes
```

hostname of the wifes computer
molly@x101:~$ hostname
x101



thanks

Jesse

---

