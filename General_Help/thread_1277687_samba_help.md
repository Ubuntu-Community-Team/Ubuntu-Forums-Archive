---
title: "samba help"
date: 2009-09-28
forum: General Help
---

### Post by davidpenta on 2009-09-28
hi,
I have got a problem related to samba
I've set up a samba server  at home.
I created a share  using SWAT. the share is accessed using a samba user I created
the problem is each time I move a folder from my windows computer to the share, once the samba server is restarted, The forementioned folder I copied lost all it's right(instead of rwx I get ???) and is not accessible anymore.
I don't have this problem with files.
please need some help

thanks in advance!!!

---

### Post by swerdna on 2009-09-28
It looks like a permissions thing. So let's focus on that.
Please post the return you get in a terminal window from these commands:
[LIST]
[*]testparm -s
[*]sudo pdebdit -L
[*]ls -l /path
[/LIST]

Regarding ls -l /path: /path is the first part of the path to the shared directory. For example if the share is at /home/bill/share, then /path would be /home/bill. Lop off the final directory and run "ls -l /path".

And FFI you might like to compare your share structure with some of these structures: [HowTo Configure a Professional File Server on a SOHO LAN]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

---

### Post by davidpenta on 2009-10-03
sorry to respond this late, I have not been around for a while

testparm -s:

```
[global]
        server string = %h server (Samba, Ubuntu)
        map to guest = Bad User
        obey pam restrictions = Yes
        passdb backend = tdbsam
        pam password change = Yes
        passwd program = /usr/bin/passwd %u
        passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
        unix password sync = Yes
        syslog = 0
        log file = /var/log/samba/log.%m
        max log size = 1000
        dns proxy = No
        usershare allow guests = Yes
        panic action = /usr/share/samba/panic-action %d
        invalid users = root

[ShareDocs]
        comment = partage de fichiers  sur ITECH-INTERNET
        path = /home/itech/shares
        username = smbclient
        valid users = smbclient, itech, ALL
        admin users = smbclient
        write list = smbclient, itech, ALL
        read only = No
        create mask = 0777
        directory mask = 0777
        inherit permissions = Yes
        hosts allow = 192.168.1.
        sync always = Yes
```

sudo pdebdit -L

```
sudo: pdebdit: command not found
```

ls -l /path

```
-rw-r--r-- 1 itech itech       0 2009-09-14 07:24 cat
-rw-r--r-- 1 root  root   344924 2009-09-30 06:31 CVS_FAQ
drwxr-xr-x 6 root  root     4096 2009-08-26 07:43 foo2zjs
-rwxrwxrwx 1 itech itech 1574092 2009-08-23 17:17 foo2zjs.tar.gz
drwxrwxrwx 9 root  root    69632 2009-10-03 11:45 shares
```

---

### Post by swerdna on 2009-10-04
I made atypo. It should have been ```
sudo pdbedit -L
```

Pending that, I can make a few comments and suggestions:

The option "= ALL" doesn't exist as far as I know.

The appended option "ALL" **implies** you want to allow literally everyone, so you should perhaps make the share "guest ok = yes"

The option "admin users" is only for the very experienced user because it allows ppl who access the share to execute commands as root, including deleting your filesystem or whatever. You can accidentally cause havoc.

IMO to activate unix password sync is very unusual for a non-domain-controller situation.

By leaving out the [global] definition ```
workgroup = something_or_other
```you invoke the default name for the workgroup which is "WORKGROUP". Did you mean to do that?

IMO a much better smb.conf [global] stanza would be this:
```
[global]
workgroup = WORKGROUP_NAME  <<== you supply this
netbios name = NETBIOS_NAME  <<== you supply this
server string =
name resolve order = bcast host lmhosts wins
map to guest = Bad User
local master = yes
os level = 33
usershare allow guests = Yes
usershare max shares = 100
usershare owner only = False
```

If you want to have everyone access the share without supplying credentials, make it like this:
```
[ShareDocs]
comment = partage de fichiers  sur ITECH-INTERNET
path = /home/itech/shares
force user = smbclient
guest ok = yes

```
You make the owner of the share to be smbclient and the group to be smbclient. Make the permissions on the share to be drwxr-xr-x [I assume here that you've created a Linux user called smbclient otherwise what you wrote makes little sense -- is that correct???]

If you require users to authenticate you simply remove the line "guest ok = yes".

FFI see these tutorials:
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")
and 
[HowTo Configure a Professional File Server on a SOHO LAN: Part II: Defining and Using File Shares]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

---

### Post by davidpenta on 2009-10-05
hi,thanks for the reply 
first off I use SWAT to set up my samba server, so this is why some global options are destroyed, yeah using the ALL option was a mean for me to allow all users to connect, since it doesn't work am gonna delete it.
I created the user  "smbclient" both on the linux system and on samba:
sudo pdbedit -L
smbclient:1001:

so am ok with that.

and the problem with the "admin user".I was aware of the threat that it implied, but as I was trying hard to make the share works, I just started trying everything.
the problem with the guest ok = " yes " param is that  if the user login without providing credentials he would be considered as a GUEST and won't be able to copy data into the share.

My aim is to prodive a passwordless share accessible from my local network

Thanks for all swerdna

---

### Post by swerdna on 2009-10-05
sharedocs as I wrote it is a passwordless share accessible to the network

---

