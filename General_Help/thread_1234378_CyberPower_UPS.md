---
title: "CyberPower UPS"
date: 2009-08-07
forum: General Help
---

### Post by mitchell2345 on 2009-08-07
Hello,

I cant find a package that will control this UPS for auto shutdown of PC.  

apcupsd does not recognize the UPS.  Is there an alternative package for Cyber Power?

Thanks,
Mitchell

---

### Post by tgalati4 on 2009-08-07
I presume it uses a USB to connect to the host machine?  Or perhaps ethernet connection?

Why don't you send an email to the manufacturer to provide a Linux driver.  I would like to see their response.

I keep my eyes open for used APC UPS's and replace the batteries.  They are cheap. They seem to work well using apcupsd.  Stay away from the platic case ones, they can catch fire.  Metal is definitely the way to go.

---

### Post by mitchell2345 on 2009-08-07
Yes it is USB.  I had the UPS working fine in CentOS and fedora.

In Cent i installed the manufactures software called PowerPanel.  But when i install the .deb file in ubuntu i get segfaults.

[http://www.cyberpowersystems.com/support/product-support.html](http://www.cyberpowersystems.com/support/product-support.html)

```
 mitchell@mythtv:/etc/nut$ pwrstatd
Segmentation fault
mitchell@mythtv:/etc/nut$ sudo /etc/init.d/pwrstatd start
 * Starting pwrstatd 1.1.2                                                                                                   [ OK ] 
mitchell@mythtv:/etc/nut$ pwrstat -status
Daemon service is not found.
mitchell@mythtv:/etc/nut$ 
```

In Cent once i started the daemon i was able to issue a pwrstat -status and all the info was there.

I was hoping there was a package for Ubuntu that would make this easier.

Mitchell

---

### Post by mitchell2345 on 2009-08-07
ahh.. nvm.  I got it.  i have to issue pwrstat -status as root:
itchell@mythtv:/etc/nut$ sudo pwrstat -status

The UPS information shows as following:

        Properties:
                Model Name...................  CP 1000D
                Rating Voltage............... 120 V
                Rating Power................. 580 Watt

        Current UPS status:
                State ....................... Normal
                Power Supply by ............. Utility Power
                Utility Voltage ............. 122 V
                Output Voltage............... 123 V
                Battery Capacity ............ 100 %
                Load ........................ 15 %
                Remaining Runtime ........... 47 min.
                Line Interaction............. None

---

### Post by tgalati4 on 2009-08-08
Good news.

---

### Post by Joe Curtis on 2011-11-10
> **mitchell2345 said:**
> Yes it is USB.  I had the UPS working fine in CentOS and fedora.

In Cent i installed the manufactures software called PowerPanel.  But when i install the .deb file in ubuntu i get segfaults.

[http://www.cyberpowersystems.com/support/product-support.html](http://www.cyberpowersystems.com/support/product-support.html)

```
 mitchell@mythtv:/etc/nut$ pwrstatd
Segmentation fault
mitchell@mythtv:/etc/nut$ sudo /etc/init.d/pwrstatd start
 * Starting pwrstatd 1.1.2                                                                                                    [ OK ] 
mitchell@mythtv:/etc/nut$ pwrstat -status
Daemon service is not found.
mitchell@mythtv:/etc/nut$ 
```In Cent once i started the daemon i was  able to issue a pwrstat -status and all the info was there.

I was hoping there was a package for Ubuntu that would make this easier.

Mitchell

> **mitchell2345 said:**
> ahh.. nvm.  I got it.  i have to issue pwrstat -status as root:
itchell@mythtv:/etc/nut$ sudo pwrstat -status


I am using Ubuntu Server 10.04.3 with Linux kernel 2.6.32-35-generic  with CyberPower's PowerPanel version 1.2.  I installed the i386 .deb  package, but every time I try to use pwrstat, it keeps coming back as  "Daemon service is not found."  Executing as root does NOT fix the  problem, however.
```
joseph@MeinKraftServer:~$ pwrstat -status
Daemon service is not found.
joe@server:~$ pwrstatd start
Segmentation fault
joe@server:~$ pwrstatd stop
Segmentation fault
joe@server:~$ pwrstatd restart
Segmentation fault
joe@server:~$

```Did I install the .deb package wrong?
(I just sudo dpkg -i powerpanel_1.2_i386.deb  it)  How can I fix this?

---

