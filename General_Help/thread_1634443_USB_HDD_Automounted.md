---
title: "USB HDD Automounted"
date: 2010-11-30
forum: General Help
---

### Post by froger on 2010-11-30
HI guys, just installed Maverick a few days ago and I'm facing a problem driving me nuts.
My setup is a desktop installation but its main purpose is to serve a media streamer over a NFS.
I have few HDs attached to the computer, some of them are USB, other SATA.
One of the disks is a 2TB Seagate USB drive formatted to NTFS.
I have the drive mounted of /etc/fstab like all other drives, but for some unknown reason, an hour or two from the system boot, this drive is automounted by the system, under media\Device, and the mount point created in fstab becomes inaccessible.
the strange thing is that the device is mounted and working on boot as /dev/sdg1 while fdisk show it as /dev/sdh1 after it was taken over by the system.

below is /etc/fstab, /etc/export and fdisk -l output.
will appreciate any help on this.
TiA.


**/etc/fstab**
```

/dev/sdb3  /home/eyal/Desktop/usenet  ntfs-3g  users,owner  0  0
/dev/sdd2  /media/music               ntfs-3g  users,owner  0  0
/dev/sdd1  /media/tv                  ntfs-3g  users,owner  0  0

/dev/sda1  /media/mv1                 ntfs-3g  users,owner  0  0
/dev/sdc1  /media/mv2                 ntfs-3g  users,owner  0  0
/dev/sde1  /media/mv3                 ntfs-3g  users,owner  0  0
/dev/sdf1  /media/mv4                 ntfs-3g  users,owner  0  0
/dev/sdg1  /media/BD                  ntfs-3g  users,owner  0  0
/media/mv1        /media/movies/mv1  bind  bind  0 0
/media/mv2        /media/movies/mv2  bind  bind  0 0
/media/mv3        /media/movies/mv3  bind  bind  0 0
/media/mv4        /media/movies/mv4  bind  bind  0 0
/media/BD        /media/movies/BD  bind  bind  0 0

```

**/etc/export**
```

/media/movies *(rw,sync,fsid=0,crossmnt,no_subtree_check)
/media/movies/mv1 *(rw,sync,no_subtree_check)
/media/movies/mv2 *(rw,sync,no_subtree_check)
/media/movies/mv3 *(rw,sync,no_subtree_check)
/media/movies/mv4 *(rw,sync,no_subtree_check)
/media/movies/BD *(rw,sync,no_subtree_check)
/media/music *(rw,sync,no_subtree_check)
/media/tv *(rw,sync,no_subtree_check)

```

**fdisk -l**
```


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x37b98d91

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      121602   976759808    7  HPFS/NTFS

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xdec2af91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       60802   488385536    7  HPFS/NTFS

Disk /dev/sdb: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0000dfcb

Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3040    24413184   83  Linux
/dev/sdb2            3040        3162      975873    5  Extended
/dev/sdb3            3162       30402   218807296    7  HPFS/NTFS
/dev/sdb5            3040        3162      975872   82  Linux swap / Solaris

Disk /dev/sdd: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8f9c798a

Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1       40795   327680000    7  HPFS/NTFS
/dev/sdd2           40795       60802   160704512    7  HPFS/NTFS

Disk /dev/sde: 1000.2 GB, 1000204886016 bytes
1 heads, 63 sectors/track, 31008336 cylinders
Units = cylinders of 63 * 512 = 32256 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x04421075

Device Boot      Start         End      Blocks   Id  System
/dev/sde1   *           2    31008256   976760032+   7  HPFS/NTFS

Disk /dev/sdf: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd6fd56c5

Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1      121601   976760001    7  HPFS/NTFS

Disk /dev/sdh: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e1545

Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1      243202  1953513472    7  HPFS/NTFS

```

---

### Post by galvatron408 on 2010-11-30
it sounds like your usb drive went to sleep (aka power save mode) and then when it woke up, it was automatically remounted under media/device. does that make sense?

look in /var/log/messages to see what it says.

---

### Post by froger on 2010-12-01
Thanks galvatron408.
from dmesg it does look like a USB issue, but I'm not sure if this is due to a power management.
The log shows a USB device disconnection and a reconnect right after.
Will try to use another port and turn off power management for usb devices.

Any ideas other than that? 
  
```

[ 1051.667366] usb 1-4: USB disconnect, address 5
[ 1063.600017] usb 1-4: new high speed USB device using ehci_hcd and address 7
[ 1063.734220] scsi9 : usb-storage 1-4:1.0
[ 1064.732649] scsi 9:0:0:0: Direct-Access     Seagate  Desktop          0130 PQ: 0 ANSI: 4
[ 1064.733308] sd 9:0:0:0: Attached scsi generic sg7 type 0
[ 1064.735663] sd 9:0:0:0: [sdh] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[ 1064.736533] sd 9:0:0:0: [sdh] Write Protect is off
[ 1064.736538] sd 9:0:0:0: [sdh] Mode Sense: 2f 08 00 00
[ 1064.736541] sd 9:0:0:0: [sdh] Assuming drive cache: write through
[ 1064.737878] sd 9:0:0:0: [sdh] Assuming drive cache: write through
[ 1064.737889]  sdh: sdh1
[ 1064.754036] sd 9:0:0:0: [sdh] Assuming drive cache: write through
[ 1064.754040] sd 9:0:0:0: [sdh] Attached SCSI disk
[ 2675.295325] lo: Disabled Privacy Extensions
[ 2982.442693] usb 1-4: USB disconnect, address 7
[ 2994.380014] usb 1-4: new high speed USB device using ehci_hcd and address 8
[ 2994.514680] scsi10 : usb-storage 1-4:1.0
[ 2995.512605] scsi 10:0:0:0: Direct-Access     Seagate  Desktop          0130 PQ: 0 ANSI: 4
[ 2995.513298] sd 10:0:0:0: Attached scsi generic sg7 type 0
[ 2995.514083] sd 10:0:0:0: [sdh] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[ 2995.514961] sd 10:0:0:0: [sdh] Write Protect is off
[ 2995.514966] sd 10:0:0:0: [sdh] Mode Sense: 2f 08 00 00
[ 2995.514969] sd 10:0:0:0: [sdh] Assuming drive cache: write through
[ 2995.517013] sd 10:0:0:0: [sdh] Assuming drive cache: write through
[ 2995.517025]  sdh: sdh1
[ 2995.540458] sd 10:0:0:0: [sdh] Assuming drive cache: write through
[ 2995.540461] sd 10:0:0:0: [sdh] Attached SCSI disk
[ 4613.611296] usb 1-4: USB disconnect, address 8
[ 4625.540521] usb 1-4: new high speed USB device using ehci_hcd and address 9
[ 4625.674979] scsi11 : usb-storage 1-4:1.0
[ 4626.673205] scsi 11:0:0:0: Direct-Access     Seagate  Desktop          0130 PQ: 0 ANSI: 4
[ 4626.675725] sd 11:0:0:0: Attached scsi generic sg7 type 0
[ 4626.679573] sd 11:0:0:0: [sdh] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[ 4626.680308] sd 11:0:0:0: [sdh] Write Protect is off
[ 4626.680313] sd 11:0:0:0: [sdh] Mode Sense: 2f 08 00 00
[ 4626.680316] sd 11:0:0:0: [sdh] Assuming drive cache: write through
[ 4626.681677] sd 11:0:0:0: [sdh] Assuming drive cache: write through
[ 4626.681689]  sdh: sdh1
[ 4626.702676] sd 11:0:0:0: [sdh] Assuming drive cache: write through
[ 4626.702680] sd 11:0:0:0: [sdh] Attached SCSI disk


```

---

### Post by galvatron408 on 2010-12-01
sorry, i was kind of answering your question previously. i should have said, that you should use labels. that way, if your drive is unplugged and plugged back in, it wouldn't matter.

here is the ubuntu doc on using labels

[https://help.ubuntu.com/community/RenameUSBDrive](https://help.ubuntu.com/community/RenameUSBDrive)

---

### Post by Grenage on 2010-12-01
I use the UUIDs of my external drives in fstab, just to rule this possibility out - but I've never actually seen it happen.

---

### Post by froger on 2010-12-01
Thanks guys.

Tried labeling the volumes, mount with UUIDs,changing the usb port, disabling HDD spin down, nothing seemed to help.
keep getting device disconnection events.

```

Dec  1 23:25:38 HTPC kernel: [ 1501.814892] usb 1-3.1: USB disconnect, address 5
Dec  1 23:25:50 HTPC kernel: [ 1513.532325] usb 1-3.1: new high speed USB device using ehci_hcd and address 7
Dec  1 23:25:50 HTPC kernel: [ 1513.626714] scsi9 : usb-storage 1-3.1:1.0
Dec  1 23:25:51 HTPC kernel: [ 1514.625295] scsi 9:0:0:0: Direct-Access     Seagate  Desktop          0130 PQ: 0 ANSI: 4
Dec  1 23:25:51 HTPC kernel: [ 1514.625873] sd 9:0:0:0: Attached scsi generic sg7 type 0
Dec  1 23:25:51 HTPC kernel: [ 1514.626807] sd 9:0:0:0: [sdh] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
Dec  1 23:25:51 HTPC kernel: [ 1514.628378] sd 9:0:0:0: [sdh] Write Protect is off
Dec  1 23:25:51 HTPC kernel: [ 1514.629687]  sdh: sdh1
Dec  1 23:25:51 HTPC kernel: [ 1514.657516] sd 9:0:0:0: [sdh] Attached SCSI disk

```

current /etc/fstab
```

UUID=5579DAF06786B4B2 /home/eyal/Desktop/usenet ntfs defaults,users,owner,locale=en_US.UTF-8 0 0
UUID=6CA7C3622FDFDE2E /media/BD ntfs defaults,users,owner,locale=en_US.UTF-8 0 0
UUID=662ADF662ADF31B3 /media/music ntfs defaults,users,owner,locale=en_US.UTF-8 0 0
UUID=6EB82098B82060B7 /media/mv1 ntfs defaults,users,owner,locale=en_US.UTF-8 0 0
UUID=3F3FCA270A7B7BF7 /media/mv2 ntfs defaults,users,owner,locale=en_US.UTF-8 0 0
UUID=7404BC5204BC1956 /media/mv3 ntfs defaults,users,owner,locale=en_US.UTF-8 0 0
UUID=08200D13200D0980 /media/mv4 ntfs defaults,users,owner,locale=en_US.UTF-8 0 0
UUID=80B2D646B2D63FF8 /media/tv ntfs defaults,users,owner,locale=en_US.UTF-8 0 0

/media/mv1 /media/movies/mv1 bind bind 0 0
/media/mv2 /media/movies/mv2 bind bind 0 0
/media/mv3 /media/movies/mv3 bind bind 0 0
/media/mv4 /media/movies/mv4 bind bind 0 0
/media/BD /media/movies/BD bind bind 0 0

```

blkid output
```

/dev/sda1: LABEL="mv1" UUID="6EB82098B82060B7" TYPE="ntfs"
/dev/sdb1: UUID="704d645f-162a-4f0d-a410-d178354946a7" TYPE="ext4"
/dev/sdb3: LABEL="usnet" UUID="5579DAF06786B4B2" TYPE="ntfs"
/dev/sdb5: UUID="aaa47016-c107-4b43-8304-edefdd5597af" TYPE="swap"
/dev/sdc1: LABEL="mv2" UUID="3F3FCA270A7B7BF7" TYPE="ntfs"
/dev/sdd1: LABEL="tv" UUID="80B2D646B2D63FF8" TYPE="ntfs"
/dev/sdd2: LABEL="music" UUID="662ADF662ADF31B3" TYPE="ntfs"
/dev/sde1: LABEL="mv3" UUID="7404BC5204BC1956" TYPE="ntfs"
/dev/sdf1: LABEL="mv4" UUID="08200D13200D0980" TYPE="ntfs"
/dev/sdh1: LABEL="BD" UUID="6CA7C3622FDFDE2E" TYPE="ntfs"

```

could it be a damaged device?

---

### Post by galvatron408 on 2010-12-01
i doubt that your drive is broken. i still suspect that you're just experiencing the seagate power save mode. 

Since labeling didn't help you, take a look at this article and the thread below it. See if it helps you.

[http://www.theinquirer.net/inquirer/news/1039498/seagate-snubs-linux](http://www.theinquirer.net/inquirer/news/1039498/seagate-snubs-linux)

oh btw, the purpose of the label is so that if a usb drive gets unplugged and plugged back in, the mount point won't change; it is sort of a neat trick so that you won't even notice the difference... or not supposed to anyway.

---

### Post by froger on 2010-12-02
Problem solved!
Well, it was the seagate power save mode indeed, thank you galvatron408 foo pointing me to the right direction.

There are several solutions around for what seems to be a long time known problem by Seagate, none of them worked for me.
The only (ugly) way to solve this problem was to create a crontab script that runs every 8 minutes and touches a file on the problematic mount point to keep the device from sleeping.

for the future Seagate victims:
```

crontab -e
*/8 * * * * touch /path/toYour/mountPoint/.SeagateStayAlive

```
galvatron408, I think the labels methods didn't do the job since labels are assigned to a device, while in this case every time the device reconnects after a power off, it gets the next available device /dev/hdg1 becomes to /dev/hdh1 . have no idea why the powered off device (hdg1) is not freed back.

---

### Post by Grenage on 2010-12-02
Glad to hear you got it sorted, although I am somewhat perplexed as to why the system is ignoring fstab's UUID-defined mount point.

---

### Post by froger on 2010-12-02
You would assume UUID should force mounting the device to the same mount point as it is the only anchor after device Id has changed, but no, have no idea...

---

### Post by galvatron408 on 2010-12-02
glad you got something going that works. labels are tied to partition, not devices; thats why it wouldn't matter what device you got next but for you, it would get ugly because, you'd end up with like a ton of devices in /proc/scsi/scsi and that has its own issues. 

so, stick with your stayalive solution. i like that one.

---

