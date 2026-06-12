---
title: "how to securely blank DVDRW?"
date: 2012-05-13
forum: General Help
---

### Post by qwertyjjj on 2012-05-13
How can I securely blank a DVDRW?
I tries using k3b to format it and it says it has succeeded but it doesn;t actually wipe the data.

---

### Post by FilterSelect on 2012-05-13
Microwave it. If possible, have the microwave outside. Don't inhale.

---

### Post by qwertyjjj on 2012-05-13
Tried this but no luck:
```

jack@jack-Inspiron-9300:~$ dvd+rw-format -blank /dev/sr0
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.1.
:-( can't locate appropriate format descriptor
* 3.4GB DVD+RW media detected.
- illegal command-line option for this media.
- you have the option to re-run dvd+rw-format with:
  -lead-out  to elicit lead-out relocation for better
             DVD-ROM compatibility, data is not affected;
  -force     to enforce new format (not recommended)
             and wipe the data.

jack@jack-Inspiron-9300:~$ dvd+rw-format -force /dev/sr0
* BD/DVD±RW/-RAM format utility by <appro@fy.chalmers.se>, version 7.1.
:-( can't locate appropriate format descriptor

```


Both k3b and brasero fail.

---

### Post by jonnyboysmithy on 2012-05-13
Well to be really secure the best way would be to destroy the dvd, instead of trying to erase it.
I like the microwave idea. THAT would work. ;)

---

### Post by qwertyjjj on 2012-05-14
> **jonnyboysmithy said:**
> Well to be really secure the best way would be to destroy the dvd, instead of trying to erase it.
I like the microwave idea. THAT would work. ;)

Can't, I'm giving them to someone else.
It's quite easy to secure erase hard drives so why not DVDRWs?

---

### Post by jerome1232 on 2012-05-14
Fill it with random data once, then format it.

assuming yours is /dev/sr0, I should urge some caution, typo's when working with block devices like this can be........... disastrous, tear-inducing events to say the least. Enjoy some ginger ale while you wait for this to finish, it'll be a bit.

```
sudo dd bs=3M if=/dev/random of=/dev/sr0 conv=notrunc,sync
```

---

### Post by Paqman on 2012-05-14
You can also use the tools in [secure-delete]("apt:secure-delete"). Delete all the data on it and:
```
sudo sfill -l -l -v -z /media/mountpoint_of_your_CD
```

This will write a single pass of zeros across the whole CD.

---

### Post by qwertyjjj on 2012-05-14
> **Paqman said:**
> You can also use the tools in [secure-delete]("apt:secure-delete"). Delete all the data on it and:
```
sudo sfill -l -l -v -z /media/mountpoint_of_your_CD
```

This will write a single pass of zeros across the whole CD.

I get this error:

```

jack@jack-Inspiron-9300:~$ df
Filesystem          1K-blocks     Used Available Use% Mounted on
/dev/sda1            56402128 29274496  24302264  55% /
udev                  1020704        4   1020700   1% /dev
tmpfs                  412340      848    411492   1% /run
none                     5120        0      5120   0% /run/lock
none                  1030848      224   1030624   1% /run/shm
/home/jack/.Private  56402128 29274496  24302264  55% /home/jack
/dev/sr0              4194314  4194314         0 100% /media/Jun 27 2009

jack@jack-Inspiron-9300:~$ sudo sfill -l -l -v -z /media/Jun\ 27\ 2009
Using /dev/urandom for random input.
Wipe mode is insecure (one pass [zero])
Wiping now ...
Creating /media/Jun 27 2009/oooooooo.ooo ... Error: No write permission for /media/Jun 27 2009. Read-only file system
Error: Could not remove temporary file /media/Jun 27 2009/oooooooo.ooo!


```

---

### Post by Paqman on 2012-05-14
> **qwertyjjj said:**
> I get this error:

```

jack@jack-Inspiron-9300:~$ df
Filesystem          1K-blocks     Used Available Use% Mounted on
/dev/sda1            56402128 29274496  24302264  55% /
udev                  1020704        4   1020700   1% /dev
tmpfs                  412340      848    411492   1% /run
none                     5120        0      5120   0% /run/lock
none                  1030848      224   1030624   1% /run/shm
/home/jack/.Private  56402128 29274496  24302264  55% /home/jack
/dev/sr0              4194314  4194314         0 100% /media/Jun 27 2009

jack@jack-Inspiron-9300:~$ sudo sfill -l -l -v -z /media/Jun\ 27\ 2009
Using /dev/urandom for random input.
Wipe mode is insecure (one pass [zero])
Wiping now ...
Creating /media/Jun 27 2009/oooooooo.ooo ... Error: No write permission for /media/Jun 27 2009. Read-only file system
Error: Could not remove temporary file /media/Jun 27 2009/oooooooo.ooo!


```

Actually ignore me, I was having a stupid. You can't just write to an optical disk like that. I'm not aware of any utilities designed for this, but you could just create an ISO file of random data (or zeroes) the same size as your disk and burn it, then blank it.

---

### Post by roelforg on 2012-05-14
LOL!
Nobody noticed that qwertyjjj didn't use sudo in his second post?
It might whine about that.

---

### Post by jerome1232 on 2012-05-14
using my dd command will work, your drive is /dev/sr0 as I thought it might be.

---

### Post by qwertyjjj on 2012-05-14
> **jerome1232 said:**
> using my dd command will work, your drive is /dev/sr0 as I thought it might be.

jack@jack-Inspiron-9300:~$ sudo dd bs=3M if=/dev/random of=/dev/sr0 conv=notrunc,sync
[sudo] password for jack: 
dd: opening `/dev/sr0': Read-only file system

---

### Post by jerome1232 on 2012-05-14
O.o, Try unmounting it first.

```
sudo umount /dev/sr0
sudo dd bs=3M if=/dev/random of=/dev/sr0 conv=notrunc,sync
```

---

### Post by matt_symes on 2012-05-14
Hi


> **roelforg said:**
> LOL!
Nobody noticed that qwertyjjj didn't use sudo in his second post?
It might whine about that.

Just to point out, if he's a member of the cdrom group then it will not matter if he does not use sudo.


```
brw-rw---- 1 root **cdrom** 11, 0 May 14 19:58 /dev/sr0
```
These are my groups.


```
matthew adm cdrom sudo audio dip plugdev fuse
```
Kind regards

---

### Post by qwertyjjj on 2012-05-15
> **jerome1232 said:**
> O.o, Try unmounting it first.

```
sudo umount /dev/sr0
sudo dd bs=3M if=/dev/random of=/dev/sr0 conv=notrunc,sync
```

jack@jack-Inspiron-9300:~$ sudo umount /dev/sr0
[sudo] password for jack: 
jack@jack-Inspiron-9300:~$ sudo dd bs=3M if=/dev/random of=/dev/sr0 conv=notrunc,sync
dd: opening `/dev/sr0': Read-only file system

---

### Post by mcduck on 2012-05-15
> **qwertyjjj said:**
> jack@jack-Inspiron-9300:~$ sudo umount /dev/sr0
[sudo] password for jack: 
jack@jack-Inspiron-9300:~$ sudo dd bs=3M if=/dev/random of=/dev/sr0 conv=notrunc,sync
dd: opening `/dev/sr0': Read-only file system

the filesystem used on optical media like CD's and DVD's (apart from DVD-RAM) is read-only by design. So it makes no difference what permissions you have.

I suggest doing what Paqman said, create an .iso image of the random data and write that to the disk.

---

### Post by qwertyjjj on 2012-05-15
I'm not sure what's wrong but when I try to burn an iso via k3b or brasero, it doesn't recognise that there is a burnable medium in the drive...even though the drive loads and lists data on it currently.

The disc definitely says dvd +rw on it

---

### Post by qwertyjjj on 2012-05-16
> **qwertyjjj said:**
> I'm not sure what's wrong but when I try to burn an iso via k3b or brasero, it doesn't recognise that there is a burnable medium in the drive...even though the drive loads and lists data on it currently.

The disc definitely says dvd +rw on it

any ideas what to try?

---

### Post by qwertyjjj on 2012-05-17
How can I see if the drive is working correctly?
Maybe it's missing drivers or something...

---

### Post by jerome1232 on 2012-05-17
You might have to scroll through the output a bit, as this will show all of your disks

```
sudo lshw -C disk
```

For example mine looks like this
```
  *-cdrom
       description: DVD-RAM writer
       product: CDDVDW SH-S223Q
       vendor: TSSTcorp
       physical id: 1
       bus info: scsi@12:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/sr1
       version: SB03
       [COLOR="Blue"]capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram[/COLOR]
       configuration: ansiversion=5 status=nodisc

```

---

