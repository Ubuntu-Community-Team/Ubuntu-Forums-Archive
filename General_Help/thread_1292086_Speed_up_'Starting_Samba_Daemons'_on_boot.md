---
title: "Speed up 'Starting Samba Daemons' on boot?"
date: 2009-10-15
forum: General Help
---

### Post by sab0tage on 2009-10-15
I have one 40gb boot drive, and one 160gb secondary drive. I have 1 shared directory, currently with 5 files shared.

It takes around 35 seconds or so to get past the 'Starting Samba Daemons' during boot.

Is there any way to speed that up? Its not a huge deal, but it seemed out of the ordinary, and i'd like to fix it if possible.

Thanks!

---

### Post by Giblet5 on 2009-10-15
> **sab0tage said:**
> I have one 40gb boot drive, and one 160gb secondary drive. I have 1 shared directory, currently with 5 files shared.

It takes around 35 seconds or so to get past the 'Starting Samba Daemons' during boot.

Is there any way to speed that up? Its not a huge deal, but it seemed out of the ordinary, and i'd like to fix it if possible.

Thanks!

Change your startup by modifying the rc2.d scripts. Make it start Samba after gdm has started. That way, there will be no wait during boot -- just during the first log in.

---

### Post by sab0tage on 2009-10-15
Thanks for the reply.

I should have mentioned that I do not use gnome. I have gdm disable at boot, and only run it manually if needed using startx.

Will your tip still help?

---

### Post by Giblet5 on 2009-10-15
> **sab0tage said:**
> Thanks for the reply.

I should have mentioned that I do not use gnome. I have gdm disable at boot, and only run it manually if needed using startx.

Will your tip still help?

Not really. The gimmick I was suggesting would only hide the Samba startup beneath the pretty gdm login screen. :)

Maybe you could find out why Samba takes so long to start.

Is the Samba drive slow (eg, USB 1.1)?

---

### Post by sab0tage on 2009-10-15
Drive one is on Primary IDE Master, Drive two is on Secondary IDE Master.

I'd really like to know why it takes so long to start. Is there some way to diagnose this?

Thanks for your help.

---

### Post by Giblet5 on 2009-10-15
> **sab0tage said:**
> Drive one is on Primary IDE Master, Drive two is on Secondary IDE Master.

I'd really like to know why it takes so long to start. Is there some way to diagnose this?

Thanks for your help.

Hmmm.

The logs are in /var/log/samba.

Maybe the samba partition is going bad? A dying drive may appear to have no errors, but the drive will retry on a bad sector around 256 times before a failure message is reported. If read works on the 250th try, it will seem ... slow.

Most newer drives have SMART logic and I think that SMART errors will show up in dmesg pretty quickly.

I presume these are PATA drives. Maybe they're old. Drives die.

I keep my Samba shares on a 1TB WD MyBook RAID1 external drive that's hooked to an ooooooooold HP laptop w/ USB 1.1 (as slow as it gets, but can still stream video to one other device at a time). Samba takes around two seconds to start on that box.

---

### Post by sab0tage on 2009-10-15
smbd log shows:

```
[2009/10/15 14:39:27,  0] smbd/server.c:main(1260)
  smbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
[2009/10/15 14:39:57,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Network is unreachable
[2009/10/15 14:40:27,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Network is unreachable
```

nmbd log:
```
[2009/10/15 14:38:34,  0] nmbd/nmbd.c:terminate(71)
  Got SIGTERM: going down...
[2009/10/15 14:39:26,  0] nmbd/nmbd.c:main(850)
  nmbd version 3.3.2 started.
  Copyright Andrew Tridgell and the Samba Team 1992-2009
```

I don't have any use for CUPS, so i'm wondering if fixing that error would solve the problem?

---

### Post by Giblet5 on 2009-10-15
> **sab0tage said:**
> smbd log shows:

I don't have any use for CUPS, so i'm wondering if fixing that error would solve the problem?


Yeah, you can remove the printer sharing part, but it looks like you have network config problems. That will cause other problems.

What's the output of ```
ifconfig
```

(HIDE YOUR IP ADDRESS!)

---

### Post by sab0tage on 2009-10-15
Here we go:

```
eth0      Link encap:Ethernet  HWaddr 00:e0:4c:10:f8:f4  
          inet addr:192.168.11.60  Bcast:192.168.11.255  Mask:255.255.255.0
          inet6 addr: fe80::2e0:4cff:fe10:f8f4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20162 errors:0 dropped:0 overruns:0 frame:0
          TX packets:15234 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:17911374 (17.9 MB)  TX bytes:1682868 (1.6 MB)
          Interrupt:17 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:65 errors:0 dropped:0 overruns:0 frame:0
          TX packets:65 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4188 (4.1 KB)  TX bytes:4188 (4.1 KB)
```

See any problems?

---

### Post by Giblet5 on 2009-10-15
> **sab0tage said:**
> Here we go:

See any problems?

No sir, but that error from Samba's log sure looked like there is one...

Have you tried turning off printer sharing in the .conf file and restarting Samba? Did that fix the problem?

---

### Post by sab0tage on 2009-10-15
Looking in /etc/samba/smb.conf
It appears that cups is not enabled/

```
########## Printing ##########

# If you want to automatically load your printer list rather
# than setting them up individually then you'll need this
#   load printers = yes

# lpr(ng) printing. You may wish to override the location of the
# printcap file
;   printing = bsd
;   printcap name = /etc/printcap

# CUPS printing.  See also the cupsaddsmb(8) manpage in the
# cupsys-client package.
;   printing = cups
;   printcap name = cups

```

However I still am seeing these errors:

```
[2009/10/15 20:11:33,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/15 20:11:33,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/15 20:26:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/15 20:26:38,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/15 20:41:33,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/15 20:41:33,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/15 20:54:18,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/15 20:54:18,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/15 21:08:36,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
[2009/10/15 21:08:36,  0] printing/print_cups.c:cups_connect(103)
  Unable to connect to CUPS server localhost:631 - Connection refused
```

I thought I had disabled CUPS by removing using sysv-rc-conf.
Initially, I wanted to configure samba manually, so I could understand it better, but I could not find a good tutorial, so I ended up starting gnome and setting up samba and shares from there. Maybe that was a mistake.

Sharing seems to be working fine, and I can live with the long bootup time if I have to. I just hate the taste of defeat.

Since i'm only sharing to a Macbook, the thought has crossed my mind to ditch samba for something more native  such as AFP.

---

