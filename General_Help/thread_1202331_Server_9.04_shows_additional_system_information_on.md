---
title: "Server 9.04 shows additional system information on first ssh login"
date: 2009-07-02
forum: General Help
---

### Post by lptr on 2009-07-02
Hi all, 

set up a new Jaunty server (32 Bit) copied over my id_dsa.pub for easier maintenance and logged in with:

> $ ssh roberts@192.168.10.154
Linux camfax 2.6.28-11-server #42-Ubuntu SMP Fri Apr 17 02:48:10 UTC 2009 i686

The programs included with the Ubuntu system are free software;
the exact distribution terms for each program are described in the
individual files in /usr/share/doc/*/copyright.

Ubuntu comes with ABSOLUTELY NO WARRANTY, to the extent permitted by
applicable law.

To access official Ubuntu documentation, please visit:
[http://help.ubuntu.com/](http://help.ubuntu.com/)

  System information as of Thu Jul  2 09:10:02 CEST 2009

  System load:  0.22               Swap usage:  0%     Users logged in: 1
  Usage of /:   0.3% of 223.56GB   Temperature: 52 C
  Memory usage: 1%                 Processes:   79

  Graph this data and manage this system at [https://landscape.canonical.com/](https://landscape.canonical.com/)

28 packages can be updated.
23 updates are security updates.

Last login: Thu Jul  2 09:09:35 2009 from 192.168.10.88

WOW! Nice feature I thought. Next time this 'feature' has gone. How can I enable to show this content every time login into via ssh?

Thanks in advance

rob*

---

### Post by nigeldodd on 2009-07-13
Very useful. I have no idea how to enable it every time. Would like to know the command that is being executed to produce the info.

Have just answered own question. To get this info type
/usr/bin/landscape-sysinfo

---

### Post by pot_roast on 2009-08-21
Yeah, that is actually pretty cool. Although I would like to have the information without the advertisement for Landscape. :)

---

### Post by sh4d0w808 on 2009-11-24
Is this feature available on desktop systems also?

---

