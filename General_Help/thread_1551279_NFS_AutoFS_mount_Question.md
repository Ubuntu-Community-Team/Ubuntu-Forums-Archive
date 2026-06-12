---
title: "NFS AutoFS mount Question"
date: 2010-08-12
forum: General Help
---

### Post by MikeyDL on 2010-08-12
I've got a Dlink DNS-321 that i'm using as a file server.  I originally setup SMB Shares and was working through those but noticed my Ubuntu main system was getting transfer rates at about 1.5MB p/sec where my PC was getting 10 to 15 MBit p/sec.  I decided to try and setup an NFS share.  Read the info at the *[SettingUPNFSHowTo]("https://help.ubuntu.com/community/SettingUpNFSHowTo")* in the Ubuntu community.  Manged to load *nfs-common* make change to the hosts.deny and hosts.allow and manually mount with the following command:

```
sudo mount 192.168.0.201://mnt/HD_a2/Video /home/mike/NFSVideo
```

It mounted fine and I was getting copy transfer rates of about 6.5 Mbit p/sec (3 times faster).  

So I decided to take the next step and follow the automount instructions.  They have you install *autofs* add a line to *auto.master* then create */etc/auto.home*.  That is where I got confused a bit because the sample line was:

```
  *             solarisbox1.company.com.au,solarisbox2.company.com.au:/export/home/&
``` 

I wasn't quite sure how to transcribe my mount situation to the above sample.  

Any tips?

---

### Post by bilkay on 2010-08-15
You need a line in auto.home something like:

joeblow  -fstype=nfs,rw,user  server:/exports/joeblow

The man page says you can use variables like $USER but I haven't had much luck with that.

If you have anything in /home, you might get some strange results.

After editing::

sudo autofs restart

---

