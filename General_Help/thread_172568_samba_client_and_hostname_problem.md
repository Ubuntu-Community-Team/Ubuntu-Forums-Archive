---
title: "samba client and hostname problem"
date: 2006-05-08
forum: General Help
---

### Post by Mitush on 2006-05-08
I have a network of several ubuntu (breezy) boxes, here is the snippet from the /etc/hosts file (file is the same on relevant hosts).
```
127.0.0.1 localhost.localdomain localhost serv1
192.168.1.254 gate
192.168.1.2 serv1
192.168.1.11 base1

```

I have samba installed on **serv1** and on **base1**. I've added few lines to the smb.conf file to start sharing the directory /opt/blah on **serv1**:

```
[opt_blah]
path = /opt/blah
available = yes
browseable = yes
public = yes
writable = yes
guest ok = yes
inherit permissions = yes
hosts allow = ALL

```

and smbclient shows that opt_blah is indeed shared:

```
root@serv1:~
smbclient -NL serv1
Anonymous login successful
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        homes           Disk      Home Directories
        print$          Disk      Printer Drivers
        opt_blah         Disk      
        IPC$            IPC       IPC Service (serv1 server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (serv1 server (Samba, Ubuntu))

```

(and 'smbclient //serv1/opt_blah' also does work).

However, if running smbclient on the _other_ host **base1**: 'smbclient -NL serv1', it does not show the share opt_blah:

```
root@base1:~$ smbclient -NL serv1
Anonymous login successful
Domain=[MSHOME] OS=[Unix] Server=[Samba 3.0.14a-Ubuntu]

        Sharename       Type      Comment
        ---------       ----      -------
        print$          Disk      Printer Drivers
        IPC$            IPC       IPC Service (base1 server (Samba, Ubuntu))
        ADMIN$          IPC       IPC Service (base1 server (Samba, Ubuntu))

```

It looks like smbclient connects to **localhost** instead of **serv1**, because
```
root@base1:~# nmblookup -B serv1 __SAMBA__
querying __SAMBA__ on 127.0.0.1
192.168.1.11 __SAMBA__<00>

```

I know resolving hostnames in Samba is tricky, but how is it possible that the hostname **serv1** is resoved into 127.0.0.1 (on **base1**), given the /etc/hosts file above?

For completenes, the /etc/resolv.conf file on **base1** is simply ```
nameserver 192.168.1.254
``` (the gateway/dsl modem).

Please help.

---

### Post by Mitush on 2006-05-09
Tried the IRC channel #samba for help, but it doesn't seem like there's lots of activity there... Still stuck.

---

### Post by Mitush on 2006-05-09
Problem solved (thanks ||cw@IRC). /etc/hosts file had localhost aliased to serv1 (on base1!), that's why samba was connecting to local daemon, instead of going to serv1.

---

### Post by chrwei on 2006-05-09
```
127.0.0.1 localhost.localdomain localhost serv1

```

if that's exactly like that in base1, then yeah, base1 is going to think serv1 is localhost

```
nameserver 192.168.1.254
``` (the gateway/dsl modem).

um, why not just make a local domain on the dns server?  or is this just a "dumb" router?

better yet, enable the WINS server in samba and let it do its thing

---

### Post by Mitush on 2006-05-09
[QUOTE=chrwei]
um, why not just make a local domain on the dns server?  or is this just a "dumb" router?

better yet, enable the WINS server in samba and let it do its thing[/QUOTE]

I don't quite understand what is a "dumb" router. 192.168.1.254 is the internal IP of the (netopia) dsl modem/router/switch with a static external IP which is used to connect to internet. As far as I understand, it doesn't have DNS running, but sends DNS requests to known external DNS servers.

Also, what is WINS?

---

