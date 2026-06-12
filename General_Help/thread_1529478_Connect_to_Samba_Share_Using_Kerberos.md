---
title: "Connect to Samba Share Using Kerberos"
date: 2010-07-12
forum: General Help
---

### Post by btrichardson on 2010-07-12
Hello All,

I have an Ubuntu server that's part of a Windows domain and requires Kerberos authentication when connecting to its Samba shares.

I have an Ubuntu desktop machine that is capable of obtaining Kerberos tickets via kinit and can successfully connect to the Samba share on my Ubuntu server using Kerberos authentication via smbclient. However, when I try to use mount.cifs such that I can establish a permanent connection to the Samba share, I get the following:

```
scrapcoder@scraptop:~$ sudo mount -t cifs //scrapserver/scrapcoder /mnt/scrapserver -o user=scrapcoder,domain=CORP,sec=krb5 --verbose

mount.cifs kernel mount options: unc=//scrapserver\scrapcoder,ver=1,rw,user=scrapcoder,domain=CORP,sec=krb5,ip=192.168.100.253
mount error(95): Operation not supported
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

If I remove "sec=krb5" from the above command I get prompted for a password, so I assume the use of krb5 security is what's causing the "Operation not supported" error. Is there some additional package I need to install in order for CIFS to support krb5 security?

Here's the relevant packages I have installed:


```
scrapcoder@scraptop:~$ aptitude search ~i | grep samba
i   samba-common                    - common files used by both the Samba server
i   samba-common-bin                - common files used by both the Samba server
scrapcoder@scraptop:~$ aptitude search ~i | grep smb
i   libsmbclient                    - shared library for communication with SMB/
i   python-smbc                     - Python bindings for Samba clients (libsmbc
i   smbclient                       - command-line SMB/CIFS clients for Unix    
i   smbfs                           - Samba file system utilities               
scrapcoder@scraptop:~$ aptitude search ~i | grep krb
i A krb5-config                     - Configuration files for Kerberos Version 5
i   krb5-user                       - Basic programs to authenticate using MIT K
i   libgssapi-krb5-2                - MIT Kerberos runtime libraries - krb5 GSS-
i   libkrb5-3                       - MIT Kerberos runtime libraries            
i   libkrb5support0                 - MIT Kerberos runtime libraries - Support l
```

--
Thanks!
Bryan

---

### Post by infestator on 2011-02-10
Hi Bryan,

If it is still actual, I have found a solution [here](http://samba.2283325.n4.nabble.com/Question-on-current-state-of-sec-krb5-integration-in-cifs-ko-td2517575.html). But it does not work for me.
```
root@server:~# mount.cifs -o sec=krb5 //server/pub tmp --verbose
mount.cifs kernel mount options: ip=192.168.1.1,unc=\\server\pub,sec=krb5,ver=1,user=root,pass=********
mount error(126): Required key not available
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)
```

--
Regards,
Alexander

---

### Post by infestator on 2011-02-10
Hi again,

I've found out. The Samba principal was server.inf, but I've used 'server' DN to mount share. If I specify FQDN server.inf all works fine:
```
# mount.cifs -o sec=krb5 //server.inf/users ./tmp/ --verbose
```

---

