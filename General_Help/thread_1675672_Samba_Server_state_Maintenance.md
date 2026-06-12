---
title: "Samba Server state: Maintenance"
date: 2011-01-25
forum: General Help
---

### Post by ghostzen on 2011-01-25
Hello all, 
my samba server' state is Maintenance.  How do I fix that?  
OS= Solaris 10

Please see status:

```

>svcs -xv samba

svc:/network/samba:default (SMB file server)
 State: maintenance since January 25, 2011 10:30:51 PM EST
Reason: Method failed repeatedly.
   See: http://sun.com/msg/SMF-8000-8Q
   See: man -M /usr/sfw/man -s 1m smbd
   See: man -M /usr/sfw/man -s 4 smb.conf
   See: /var/svc/log/network-samba:default.log
Impact: This service is not running.

```

```


cat /var/svc/log/network-samba\:default.log | tail -3  

[ Jan 25 21:31:57 Executing stop method ("/usr/bin/kill `cat /var/samba/locks/smbd.pid`") ]
kill: 1310: no such process
[ Jan 25 21:44:57 Method "stop" exited with status 2 


```

I have restarted smbd and nmbd and run testparm to every change I made to smb.conf.  There was no error.  I have also rebooted and still no luck.  Your help is very much appreciated. 

-GZ

---

### Post by capscrew on 2011-01-26
> **ghostzen said:**
> Hello all, 
my samba server' state is Maintenance.  How do I fix that?  
OS= Solaris 10

Please see status:

```

>svcs -xv samba

svc:/network/samba:default (SMB file server)
 State: maintenance since January 25, 2011 10:30:51 PM EST
Reason: Method failed repeatedly.
   See: http://sun.com/msg/SMF-8000-8Q
   See: man -M /usr/sfw/man -s 1m smbd
   See: man -M /usr/sfw/man -s 4 smb.conf
   See: /var/svc/log/network-samba:default.log
Impact: This service is not running.

```

```


cat /var/svc/log/network-samba\:default.log | tail -3  

[ Jan 25 21:31:57 Executing stop method ("/usr/bin/kill `cat /var/samba/locks/smbd.pid`") ]
kill: 1310: no such process
[ Jan 25 21:44:57 Method "stop" exited with status 2 


```

I have restarted smbd and nmbd and run testparm to every change I made to smb.conf.  There was no error.  I have also rebooted and still no luck.  Your help is very much appreciated. 

-GZ

This ***[COLOR="Purple"]Sun Solaris[/COLOR]*** setup looks to be implemented differently  than that of an Ubuntu install.

See [**_[COLOR="Blue"]here[/COLOR]_**]("http://www.unix.com/solaris/132874-samba-solaris-10-issue.html") for some thoughts.

It looks like if there is a failure of a sub-system Samba is put in a *Sun described* maintenance mode.  I would carefully look at all of the logs for Samba to see what is failing to load properly.

---

### Post by ghostzen on 2011-02-05
Thank you.

Sorry for the late reply.  My coworker gave me a cloned Solaris samba server's VM, which was crappy and out of date.  I ended up reinstalled Samba server and it worked.  

Thanks again

---

