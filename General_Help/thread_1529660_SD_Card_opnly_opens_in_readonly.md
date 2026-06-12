---
title: "SD Card opnly opens in readonly"
date: 2010-07-12
forum: General Help
---

### Post by p0is0n on 2010-07-12
Hi all,
I am trying to write a file to a SD card in my card reader.
When Ubuntu first boots in and I open up the SD card It gives the option to create folders and files. However after a second or two the window closes and then will only let me vew the files.

Does anyone know how I can fix this so that the SD card is able to be written to?

The lock is not on the SD card, and under permissions it states that I have permission to create and delete files.

I am using an up to date version of Ubuntu Lucid Lynx 10.04
I have tried searching for a solution but cannot find anything relevant that works

Any help would be appreciated.
Thanks!

Edit :
output of syslog from removing and reinserting the SD card
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.332963] sd 10:0:0:0: [sdd] 3970048 512-byte logical blocks: (2.03 GB/1.89 GiB)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.333707] sd 10:0:0:0: [sdd] Assuming drive cache: write through
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.335080] sd 10:0:0:0: [sdd] Assuming drive cache: write through
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.335084]  sdd: sdd1
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651437] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651440]     invalid access to FAT (entry 0xcdcba4b7)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651442]     File system has been set read-only
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651920] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651922]     invalid access to FAT (entry 0xe13f7a2c)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.652890] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.652892]     invalid access to FAT (entry 0xf54ba19c)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.653558] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.653559]     invalid access to FAT (entry 0x1fde9987)
Jul 12 19:19:38 p0is0n-desktop kernel: [ 1140.881577] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:38 p0is0n-desktop kernel: [ 1140.881580]     invalid access to FAT (entry 0xcdcba4b7)
Jul 12 19:19:38 p0is0n-desktop kernel: [ 1140.884416] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:38 p0is0n-desktop kernel: [ 1140.884418]     invalid access to FAT (entry 0xe13f7a2c)

I see there are errors but have no idea what they mean or how to fix.

---

### Post by dragos240 on 2010-07-12
> **p0is0n said:**
> Hi all,
I am trying to write a file to a SD card in my card reader.
When Ubuntu first boots in and I open up the SD card It gives the option to create folders and files. However after a second or two the window closes and then will only let me vew the files.

Does anyone know how I can fix this so that the SD card is able to be written to?

The lock is not on the SD card, and under permissions it states that I have permission to create and delete files.

I am using an up to date version of Ubuntu Lucid Lynx 10.04
I have tried searching for a solution but cannot find anything relevant that works

Any help would be appreciated.
Thanks!

Edit :
output of syslog from removing and reinserting the SD card
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.332963] sd 10:0:0:0: [sdd] 3970048 512-byte logical blocks: (2.03 GB/1.89 GiB)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.333707] sd 10:0:0:0: [sdd] Assuming drive cache: write through
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.335080] sd 10:0:0:0: [sdd] Assuming drive cache: write through
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.335084]  sdd: sdd1
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651437] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651440]     invalid access to FAT (entry 0xcdcba4b7)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651442]     File system has been set read-only
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651920] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.651922]     invalid access to FAT (entry 0xe13f7a2c)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.652890] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.652892]     invalid access to FAT (entry 0xf54ba19c)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.653558] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:19 p0is0n-desktop kernel: [ 1122.653559]     invalid access to FAT (entry 0x1fde9987)
Jul 12 19:19:38 p0is0n-desktop kernel: [ 1140.881577] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:38 p0is0n-desktop kernel: [ 1140.881580]     invalid access to FAT (entry 0xcdcba4b7)
Jul 12 19:19:38 p0is0n-desktop kernel: [ 1140.884416] FAT: Filesystem error (dev sdd1)
Jul 12 19:19:38 p0is0n-desktop kernel: [ 1140.884418]     invalid access to FAT (entry 0xe13f7a2c)

I see there are errors but have no idea what they mean or how to fix.

sudo umount /dev/sdd1
sudo fsck /dev/sdd1

Reboot. Tell me if it works.

---

### Post by p0is0n on 2010-07-12
> **dragos240 said:**
> sudo umount /dev/sdd1
sudo fsck /dev/sdd1

Reboot. Tell me if it works.

Thanks for the reply.
I have run those commands and the same problem is occurring.
For the few seconds it shows the options to create files and folders if tried it spits out an message saying that the device is read-only.

rm: cannot remove `Filename.file': Read-only file system

---

### Post by dragos240 on 2010-07-12
> **p0is0n said:**
> Thanks for the reply.
I have run those commands and the same problem is occurring.
For the few seconds it shows the options to create files and folders if tried it spits out an message saying that the device is read-only.

rm: cannot remove `Filename.file': Read-only file system

Looks like an improper mount to me. Can you mount any other USB devices?

---

### Post by p0is0n on 2010-07-12
> **dragos240 said:**
> Looks like an improper mount to me. Can you mount any other USB devices?

It isn't a usb cardreader, it's built in, connects straight to the motherboard.
I don't have another SD card to test, but a memory stick card worked just fine (uses a different slot on the card reader though).

---

### Post by dragos240 on 2010-07-12
> **p0is0n said:**
> It isn't a usb cardreader, it's built in, connects straight to the motherboard.
I don't have another SD card to test, but a memory stick card worked just fine (uses a different slot on the card reader though).

Yeah, I was testing the mount features. Hmm. One other thing I can think of is this. Do this:
sudo mount /dev/sdb /mnt
sudo chown -R yourusername /mnt/*
chmod +rw /mnt/*

---

### Post by p0is0n on 2010-07-12
> **dragos240 said:**
> Yeah, I was testing the mount features. Hmm. One other thing I can think of is this. Do this:
sudo mount /dev/sdb /mnt
sudo chown -R yourusername /mnt/*
chmod +rw /mnt/*

When doing sudo mount /dev/sdd /mnt I get :
mount: /dev/sdd already mounted or /mnt busy

umount  dev/sdd gives :
umount: dev/sdd is not mounted (according to mtab)

Edit:
Ok so after some playing when mounting :
sudo mount /dev/sdd /mnt
I get :
mount: you must specify the filesystem type
so I do :
sudo mount /dev/sdd /mnt -t msdos
and get :
mount: wrong fs type, bad option, bad superblock on /dev/sdd,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail gives :
[ 4094.940906] FAT: bogus number of reserved sectors
[ 4094.940910] VFS: Can't find a valid FAT filesystem on dev sdd.
[ 4098.218335] FAT: bogus number of reserved sectors
[ 4098.218340] VFS: Can't find a valid FAT filesystem on dev sdd.
[ 4145.965467] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 239
[ 4177.299564] FAT: bogus number of reserved sectors
[ 4177.299569] VFS: Can't find a valid FAT filesystem on dev sdd.
[ 4205.909901] ===>rt_ioctl_giwscan. 1(1) BSS returned, data->length = 239
[ 4223.280393] FAT: bogus number of reserved sectors
[ 4223.280399] VFS: Can't find a valid FAT filesystem on dev sdd.

:S

---

### Post by t0p on 2010-07-12
I've experienced this problem a few times, and invariably the reason has been a faulty memory card or stick. If you go back to the retailer they will replace the card without much question.

---

### Post by p0is0n on 2010-07-12
> **t0p said:**
> I've experienced this problem a few times, and invariably the reason has been a faulty memory card or stick. If you go back to the retailer they will replace the card without much question.

I have had this card for about 3 years with no previous problems. Doubt I can take it back now :p
If the problem is the card, that is fine I can get a new one.
I just don't want to get a new one and come back to the same problem lol.

---

### Post by p0is0n on 2010-07-12
Well my problem is now solved.

I tested the card in windows and it popped up do you want to repair, yes, done, into linux again and all is working just fine :o

Oh well I guess that windows install is good for something at least lol.

Thanks for all the help and suggestions!

---

### Post by p0is0n on 2010-07-12
Just an update on this.
I still have no solution for repairing the SD card in linux, however I found the source of the problem/corruption.

I am using the SD card on an opensource handheld console the GP2X (runs linux).
The problem was some applications/games were running from the SD card and not unmounting the SD card after finishing execution.

My games are run from a script that mounts the SD card then runs the game and on return from execution of the game unmounts the SD card and returns to the main menu.

I can just wrap the ones I use in a similar script to prevent any further problems.

It seems like linux mounts the filesystem in a readonly state if it previously encountered a problem whereas windows just opens it in read/write mode regardless of any previous errors.

---

