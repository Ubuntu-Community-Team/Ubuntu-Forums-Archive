---
title: "Can't format my fc hard drive"
date: 2010-09-08
forum: General Help
---

### Post by bdemers on 2010-09-08
Below is results from attempt at formatting my hard drive. As you can see a driver is installed, but not working.  Perhaps something is missing?
Seems a bit odd that a "unable to read" comes back when disk data is reported.  The drive just went through a low level format.

BTW this is a fiber channel drive.  Also on board are 5 scsi drives.  Adaptec raid card.  Not sure if that would have any relevence, but there you are.


barry@vm1:~$ sudo lshw -C disk
  *-disk                  
       description: SCSI Disk
       product: ST173404 CLAR72
       vendor: SEAGATE
       physical id: 0.0.0
       bus info: scsi@1:0.0.0
       logical name: /dev/sdb
       version: 3A98
       serial: 3CE0SRYL00007142FHAW
       capacity: 67GiB (72GB)
       capabilities: 10000rpm
       configuration: ansiversion=3
barry@vm1:~$ sudo fdisk /dev/sdb

Unable to read /dev/sdb
barry@vm1:~$ modprobe qla2xxx
barry@vm1:~$ lsmod|grep qla2xxx
qla2xxx               177252  0 
scsi_transport_fc      45192  1 qla2xxx
scsi_mod              151308  10 sr_mod,sg,sd_mod,aic7xxx,qla2xxx,scsi_transport_fc,scsi_transport_spi,aacraid,scsi_tgt,libata
barry@vm1:~$ dmesg|tail
[ 1362.775343] AAC:ID(0:06:0); Error Event [command:0x1a]
[ 1362.775716] AAC:ID(0:06:0); Illegal Request [k:0x5,c:0x0,q:0x0]
[ 1362.776090] AAC:ID(0:06:0); No Additional Sense Information
[ 2053.143084] end_request: I/O error, dev fd0, sector 0
[ 2053.167071] end_request: I/O error, dev fd0, sector 0
[ 2087.341326] end_request: I/O error, dev fd0, sector 0
[ 2087.365339] end_request: I/O error, dev fd0, sector 0
[ 2373.652883] AAC:ID(0:06:0); Error Event [command:0x1a]
[ 2373.653256] AAC:ID(0:06:0); Illegal Request [k:0x5,c:0x0,q:0x0]
[ 2373.653636] AAC:ID(0:06:0); No Additional Sense Information
barry@vm1:~$

---

### Post by lukeiamyourfather on 2010-09-08
I'd suggest trying GParted. If using a server with only CLI, connect via SSH and use X tunneling. Though you'll need to install GParted first.

```

sudo apt-get install gparted

```

```

ssh -X user@host

```

---

### Post by bdemers on 2010-09-08
Good try. I had installed GParted prior to the terminal.. No luck.  GParted doesn't even report the existence of that drive!

---

### Post by lukeiamyourfather on 2010-09-08
I've had good luck with Adaptec cards in Linux so hopefully that's not the issue. Have you tried the disk in another system to see if the disk itself is bad?

---

### Post by bdemers on 2010-09-08
As I said, I just got done with a low level format, drive is fine.  I am currently upgrading to 10.04 since I just found a bug report stating that there is some issue with firmware that has been addressed.  I'll report back in an hour or so.

---

