---
title: "Boot Time Error[11.10]"
date: 2012-04-27
forum: General Help
---

### Post by pawanthegunner on 2012-04-27
O.K, so this was a hellish day for me. I was running updates and there  was power faliure (my ups is pretty messed up). so i re-booted in and  ran 
```
sudo dpkg --configure -a
```as i always do to resume updates.  But then again, right as i hit return, there was power faliure.
when i rebooted again, i had the grub screen with several options, i  chose the top one(not recovery mode) and it took me to BusyBox inramfs  or something like that.
all this time the caps-lock and num-lock indicators were blinking.

now i can't boot into my OS. I have only ubuntu 11.10 installed and only have one partition of the filesystem apart from swap.

when i boot from livecd and try to mount the filesystem, it shows :
```
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

``````
dmesg | tail
```gives following result :

```
ubuntu@ubuntu:~$ dmesg | tail
[ 1051.676347] Descriptor sense data with sense descriptors (in hex):
[ 1051.676350]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 1051.676365]         04 84 35 42 
[ 1051.676372] sd 2:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[ 1051.676380] sd 2:0:0:0: [sda] CDB: Read(10): 28 00 04 84 34 60 00 00 f0 00
[ 1051.676395] end_request: I/O error, dev sda, sector 75773250
[ 1051.676407] JBD: Failed to read block at offset 1448
[ 1051.676418] JBD: recovery failed
[ 1051.676423] EXT4-fs (sda1): error loading journal
[ 1051.676426] ata3: EH complete
```trying to mount from terminal gives :
```
ubuntu@ubuntu:~$ sudo mount /dev/sda1
mount: can't find /dev/sda1 in /etc/fstab or /etc/mtab

```i dont want to reinstall and lose thousands of MB of data...is there a way out of this?

---

### Post by Rubi1200 on 2012-04-28
Closed.

Duplicate thread here:
[http://ubuntuforums.org/showthread.php?t=1966856](http://ubuntuforums.org/showthread.php?t=1966856)

Please don't post the same question multiple times, it dilutes community effort to help you.

---

