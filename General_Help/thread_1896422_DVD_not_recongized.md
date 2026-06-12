---
title: "DVD not recongized"
date: 2011-12-16
forum: General Help
---

### Post by yoramdavid on 2011-12-16
Hello all,

I inserted a DVD (Video movie) in the drive but it was not recognizes, I cannot see anything (it is not mounted), nor can I eject it.
I tried to eject it from the disk utility but there is no "No media in drive" error. Nor can I eject if pressing the eject button on the drive itself.

I used the drive before and it worked fine.

Any ideas?

Yoram, with thanks.

---

### Post by bluexrider on 2011-12-16
> **yoramdavid said:**
> Hello all,

I inserted a DVD (Video movie) in the drive but it was not recognizes, I cannot see anything (it is not mounted), nor can I eject it.
I tried to eject it from the disk utility but there is no "No media in drive" error. Nor can I eject if pressing the eject button on the drive itself.

I used the drive before and it worked fine.

Any ideas?

Yoram, with thanks.

There should be a small hole in the faceplate of the CD-rom drive,  unfold a paperclip and insert it in the hole and push until the drive  pops open.

I don't recommend this as a permanent fix but its quick. Obviously having a mounting problem. Does the drive show up in file manager?

```
sudo lshw -C disk; sudo lshw -C drive; lsb_release -a
```

---

### Post by yoramdavid on 2011-12-16
> **bluexrider said:**
> There should be a small hole in the faceplate of the CD-rom drive,  unfold a paperclip and insert it in the hole and push until the drive  pops open.

I don't recommend this as a permanent fix but its quick. Obviously having a mounting problem. Does the drive show up in file manager?

```
sudo lshw -C disk; sudo lshw -C drive; lsb_release -a
```

Thank you bluexrider,

So that is what this litte hole is there for? It did it, indeed.
Now the drive ejected the DVD, it was spinning, I had to take the DVD off with it spinning. The led is still lit up now that the drive is back inside and empty. It still does not eject.

No it did not appear in the file manager at all. and there is no entry for it in the etc/fstab.

```
~$ sudo lshw -C disk; sudo lshw -C drive; lsb_release -a
PCI (sysfs)  
Codename:	oneiric
yoram@yoram-II:~$ sudo lshw -C disk; sudo lshw -C drive; lsb_release -a
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD A  DS8AZH
       vendor: Slimtype
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom1
       logical name: /dev/cdrw1
       logical name: /dev/dvd1
       logical name: /dev/dvdrw1
       logical name: /dev/scd0
       logical name: /dev/sr0
       version: NH61
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=busy
  *-disk
       description: ATA Disk
       product: FUJITSU MHV2120B
       vendor: Fujitsu
       physical id: 0.0.0
       bus info: scsi@2:0.0.0
       logical name: /dev/sda
       version: 892C
       serial: NW9XT723ASWF
       size: 111GiB (120GB)
       capabilities: partitioned partitioned:dos
       configuration: ansiversion=5 signature=5b3c897a
LSB Version:    core-2.0-amd64:core-2.0-noarch:core-3.0-amd64:core-3.0-noarch:core-3.1-amd64:core-3.1-noarch:core-3.2-amd64:core-3.2-noarch:core-4.0-amd64:core-4.0-noarch
Distributor ID:	Ubuntu
Description:	Ubuntu 11.10
Release:	11.10
Codename:	oneiric
```

There was one thing weird about getting this code, first it showed up some results, then there was the "PCIsysfs" coming up again and when it showed the rest of the code, the first part was gone (blank lines).The bits missing were those:
```
yoram@yoram-II:~$ sudo lshw -C disk; sudo lshw -C drive; lsb_release -a
  *-cdrom                 
       description: DVD-RAM writer
       product: DVD A  DS8AZH
       vendor: Slimtype
       physical id: 0.0.0
```

---

### Post by bluexrider on 2011-12-16
you can see the results under *-cdrom status was busy. it was trying to work.

use a known good CD or DVD and try it again after rebooting.

it should work because your devices are listed

       logical name: /dev/cdrom1        
logical name: /dev/cdrw1        
logical name: /dev/dvd1        
logical name: /dev/dvdrw1        
logical name: /dev/scd0        
logical name: /dev/sr0

---

### Post by yoramdavid on 2011-12-17
> **bluexrider said:**
> you can see the results under *-cdrom status was busy. it was trying to work.

Thank you bluexrider,

That code was generated with the DVD out of the drive, so it was busy trying to work without DVD in. It is still now... according to the led which is on.
I will try rebooting my system and inserting another DVD.

Yoram

---

### Post by bluexrider on 2011-12-17
> **yoramdavid said:**
> Thank you bluexrider,

That code was generated with the DVD out of the drive, so it was busy trying to work without DVD in. It is still now... according to the led which is on.
I will try rebooting my system and inserting another DVD.

Yoram


Okay, keep us posted...

---

### Post by yoramdavid on 2011-12-17
> **bluexrider said:**
> Okay, keep us posted...

Okay,

Rebooted, inserted a different DVD, and I was able to browse and eject.
I was not able to play the DVD, the system got very slow. I have problems with my Ubuntu installation, but that is another story.

I guess I'll mark this threat as solved then, since I am assuming it was a bad DVD.

Thank you once more.

Yoram

---

### Post by bluexrider on 2011-12-17
> **yoramdavid said:**
> Okay,

Rebooted, inserted a different DVD, and I was able to browse and eject.
I was not able to play the DVD, the system got very slow. I have problems with my Ubuntu installation, but that is another story.

I guess I'll mark this threat as solved then, since I am assuming it was a bad DVD.

Thank you once more.

Yoram
Good thing, 

happy *buntu

---

