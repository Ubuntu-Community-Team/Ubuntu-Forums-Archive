---
title: "Need help mounting netware partition"
date: 2010-04-19
forum: General Help
---

### Post by oneilchung on 2010-04-19
I have an old HDD with my custom written accounts software running on novell netware 3.11 on it.

The computer it's running on died and as the system run on BNC cables, I can no longer find a machine that will support it. So effectively I have no way to access my data.

So I attached the HDD onto my ubuntu machine but there is no way to mount it. Searching through the forum, there is absolutely no reference to any means on mounting the HDD also.

I'm quite new to the ubuntu scene so I was hoping that some of you Gurus out there might point me in the right direction. 

This is my testdisk printout.....

```
TestDisk 6.11, Data Recovery Utility, April 2009
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 4311 MB / 4112 MiB - CHS 524 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * FAT16 >32M               0   1  1    12 254 63     208782 [NO NAME]
 2 P NetWare 3.11+           13   0  1   523 254 63    8209215











*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

```

what I am trying to achieve is to mount the netware partition... Please help...

---

### Post by dcstar on 2010-04-20
> **oneilchung said:**
> I have an old HDD with my custom written accounts software running on novell netware 3.11 on it.
......
what I am trying to achieve is to mount the netware partition... Please help...

It looks like the nwfs support disappeared from the Linux kernel about 10 years ago, perhaps Novell go ansty with the legalities of it?

---

### Post by oneilchung on 2010-04-20
:-({|=

So basically I'm dead without hopes of salvation on the matter?? 4years of data........

---

### Post by oneilchung on 2010-04-20
Oh, and thanks and respect to David. I've managed to get some headway after knowing that the file system is in nwfs.... Sorry for being the noob on this.... 

But never really thought I'd have to deal with such prehistoric stuff until the auditors came knocking

---

### Post by new_tolinux on 2010-04-20
I don't know if Ubuntu is doing any nwfs-support, but it's possible to make a fully patched NW312 server run on VMWare.
It is also possible to connect to NW312 in OpenSuse. Probably also in Ubuntu, but I don't know that.

This is what I read about opensuse -> 3.12 connections: [http://forums.opensuse.org/get-help-here/network-internet/437013-ipx-protocol.html](http://forums.opensuse.org/get-help-here/network-internet/437013-ipx-protocol.html)

---

### Post by oneilchung on 2010-04-22
Thanks for all the help~

Installed Open SUSE on a spare computer I had and viola, I mounted the HDD with no problems. Took me a few frustrating days but at least it got solved.

Thanks for the open suse tip.

---

### Post by netwatcher_s1 on 2011-06-22
Hello. I know this post is old but I have similar problem.  I have Netware 4.11 hard drives with data on them and I would like to retrieve it in SUSE Linux Enterprise Server or something similar, perhaps Ubuntu.  Anything will do.

You mention you were able to get it working on Open SUSE.  Can you explain what you did to get it working?

Thank you in advance,
Justin

---

