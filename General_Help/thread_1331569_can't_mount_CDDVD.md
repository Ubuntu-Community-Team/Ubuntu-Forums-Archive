---
title: "can't mount CD/DVD"
date: 2009-11-19
forum: General Help
---

### Post by beacon on 2009-11-19
On occasion a CD or DVD will mount, but most of the time it will not. There seem to be several different messages when I try. The most recent is 'unable to mount location; can't mount file'. I have checked various things according to other postings and have the following if it helps:

X-desktop:~$ sudo mkdir /mnt/cdrom
[sudo] password for X: 
X-desktop:~$ sudo mkdir /mnt/cdrom
mkdir: cannot create directory `/mnt/cdrom': File exists
X-desktop:~$ sudo mount /dev/scd0 -t iso9660 /mnt/cdrom
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

X-desktop:~$ ls /mnt/cdrom
X-desktop:~$ dmesg | tail
[   21.080788] vboxdrv: Found 2 processor cores.
[   21.080867] vboxdrv: fAsync=1 offMin=0x165e2f offMax=0x165e2f
[   21.080921] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   21.080923] vboxdrv: Successfully loaded version 2.1.4_OSE (interface 0x000a0009).
[   22.163753] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.163756] Bluetooth: BNEP filters: protocol multicast
[   22.193526] Bridge firewalling registered
[   37.444024] eth0: no IPv6 routers present
[   83.181432] ISO 9660 Extensions: RRIP_1991A
[  308.527680] ISOFS: Unable to identify CD-ROM format.

Probably the next disk I insert will produce yet a different message. I wonder if anyone has suggestions that may help.

With thanks.

---

