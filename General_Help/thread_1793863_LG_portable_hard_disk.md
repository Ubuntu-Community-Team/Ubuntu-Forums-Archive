---
title: "LG portable hard disk"
date: 2011-06-30
forum: General Help
---

### Post by shamz_71 on 2011-06-30
My laptop (Acer aspire 4920 ) running  Ubuntu ( 11.04 ) cant detect LG portable hard disk .
Any solutions?

---

### Post by blueridgedog on 2011-06-30
Is is USB?

Can you post the output of 

```
lsusb
```

While the disk is connected?

---

### Post by shamz_71 on 2011-07-05
> **blueridgedog said:**
> Is is USB?

Can you post the output of 

```
lsusb
```While the disk is connected?

farooq@KhalidTank:~$ lusb
No command 'lusb' found, did you mean:
 Command 'lush' from package 'lush' (universe)
 Command 'lsusb' from package 'usbutils' (main)
lusb: command not found


Also i have noticed my cd rom doesnt read disks

---

### Post by Wim Sturkenboom on 2011-07-05
it is *l**[COLOR="Red"]s[/COLOR]**usb*

copy the code previously given (after connecting the external hd)

Is it working on another system (if you have one)? If your laptop is dual boot, does it work with the other OS?

---

### Post by shamz_71 on 2011-07-07
farooq@KhalidTank:~$ lsusb
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 1532:0016 Razer USA, Ltd 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 043e:70f1 LG Electronics USA, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a101 Suyin Corp. Acer CrystalEye Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub



Yes the USB HD works on windows machine. I m not running dual boot

---

### Post by Wim Sturkenboom on 2011-07-07
So it looks like it's detected. Please post the output of *dmesg | tail -n15* immediately after you've inserted the HD; you should see something with 'scsi', sdX (x being a number).

---

### Post by shamz_71 on 2011-07-07
farooq@KhalidTank:~$ dmesg | tail -n15 
[   29.937653] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   29.937656] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   29.937658] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   29.937661] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   29.937663] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   29.937666] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   29.937669] cfg80211: Regulatory domain changed to country: AT
[   29.937671] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   29.937673] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.937676] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.937679] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   29.937681] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   31.938997] Intel AES-NI instructions are not detected.
[   31.950528] padlock_aes: VIA PadLock not detected.
[   40.656031] wlan0: no IPv6 routers present

---

### Post by Wim Sturkenboom on 2011-07-07
hmm, at a loss

The below is what you're supposed to see after inserting the drive
```

[65253.850029] usb 2-1: new high speed USB device using ehci_hcd and address 2
[65254.002823] usb 2-1: configuration #1 chosen from 1 choice
[65254.043682] Initializing USB Mass Storage driver...
[65254.043867] scsi6 : SCSI emulation for USB Mass Storage devices
[65254.043953] usb-storage: device found at 2
[65254.043955] usb-storage: waiting for device to settle before scanning
[65254.043966] usbcore: registered new interface driver usb-storage
[65254.043969] USB Mass Storage support registered.
[65259.040104] usb-storage: device scan complete
[65259.040459] scsi 6:0:0:0: Direct-Access     CBM      Flash Disk       5.00 PQ: 0 ANSI: 2
[65259.040846] sd 6:0:0:0: Attached scsi generic sg2 type 0
[65259.042337] sd 6:0:0:0: [sdb] 2062336 512-byte logical blocks: (1.05 GB/1007 MiB)
[65259.042819] sd 6:0:0:0: [sdb] Write Protect is off
[65259.042823] sd 6:0:0:0: [sdb] Mode Sense: 0b 00 00 08
[65259.042825] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[65259.044570] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[65259.044573]  sdb: sdb1
[65259.046701] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[65259.046705] sd 6:0:0:0: [sdb] Attached SCSI removable disk

```

---

### Post by shamz_71 on 2011-07-08
tail -n15
[   32.138443] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   32.138446] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[   32.138448] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   32.138451] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[   32.138454] cfg80211: 2402000 KHz - 2482000 KHz @  KHz), (N/A mBi, 2000 mBm)
[   32.138457] cfg80211: Regulatory domain changed to country: AT
[   32.138459] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   32.138461] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.138464] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.138467] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[   32.138469] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[   32.303521] Intel AES-NI instructions are not detected.
[   32.318222] padlock_aes: VIA PadLock not detected.
[   42.688057] wlan0: no IPv6 routers present
[  707.888112] usb 2-5: USB disconnect, address 3
farooq@KhalidTank:~$ dmesg | tail -n15
[  746.512125] usb 2-5: new high speed USB device using ehci_hcd and address 4
[  746.649600] scsi5 : usb-storage 2-5:1.0
[  747.648978] scsi 5:0:0:0: Direct-Access     TOSHIBA  MK3259GSX             PQ: 0 ANSI: 2 CCS
[  747.651007] sd 5:0:0:0: Attached scsi generic sg2 type 0
[  747.653677] sd 5:0:0:0: [sdb] 625142448 512-byte logical blocks: (320 GB/298 GiB)
[  747.654415] sd 5:0:0:0: [sdb] Write Protect is off
[  747.654423] sd 5:0:0:0: [sdb] Mode Sense: 28 00 00 00
[  747.655550] sd 5:0:0:0: [sdb] Incomplete mode parameter data
[  747.655558] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  747.659055] sd 5:0:0:0: [sdb] Incomplete mode parameter data
[  747.659064] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  747.681453]  sdb: sdb1
[  747.684291] sd 5:0:0:0: [sdb] Incomplete mode parameter data
[  747.684296] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[  747.684299] sd 5:0:0:0: [sdb] Attached SCSI disk

---

### Post by Wim Sturkenboom on 2011-07-08
Ha, there is some hope ;)

Let's see if it is already mounted but not showing on the desktop

```

wim@ubuntuserver:~$ **cat /etc/mtab**
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
none /var/lib/ureadahead/debugfs debugfs rw,relatime 0 0
/dev/sda5 /home ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/wim/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=wim 0 0
[COLOR="Red"][B]/dev/sdb1 /media/DISK_IMG vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
[/B][/COLOR]
```

In this case, it's mounted on /media/DISK_IMG (the latter being the label of the disk, so it might be different for yours). Let me know if it's there or not.

A *ls* will reveal the content

```

wim@ubuntuserver:~$ **ls -l /media/DISK_IMG/**
total 32
drwx------ 2 wim wim 16384 2010-12-20 15:27 Tokina_EL28_20101220
drwx------ 2 wim wim 16384 2011-01-18 17:30 vivitar_55macro_20101229

// do your work on the disk here

```

I can not help you with the problem why it does not show on the desktop; somebody else might be able to.

If it's not yet mounted, you can mount it on e.g. /mnt
```

wim@ubuntuserver:~$ **sudo mount /dev/sdb1 /mnt**
wim@ubuntuserver:~$ **ls -l /mnt**
total 32
drwx------ 2 wim wim 16384 2010-12-20 15:27 Tokina_EL28_20101220
drwx------ 2 wim wim 16384 2011-01-18 17:30 vivitar_55macro_20101229

// do your work with the disk here

wim@ubuntuserver:~$ **sudo umount /mnt**

// safe to remove the drive

```

If the above works, at least you have access. I'm not a desktop man, so others will hopefully jump in to get the rest sorted.

---

### Post by shamz_71 on 2011-07-08
what commands/steps to do now?
i cant understand the above , kindly simplify

---

### Post by shamz_71 on 2011-07-08
> **Wim Sturkenboom said:**
> Ha, there is some hope ;)

Let's see if it is already mounted but not showing on the desktop

[code]
wim@ubuntuserver:~$ **cat /etc/mtab**
/dev/sda1 / ext4 rw,errors=remount-ro 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
none /sys sysfs rw,noexec,nosuid,nodev 0 0
none /sys/fs/fuse/connections fusectl rw 0 0
none /sys/kernel/debug debugfs rw 0 0
none /sys/kernel/security securityfs rw 0 0
none /dev devtmpfs rw,mode=0755 0 0
none /dev/pts devpts rw,noexec,nosuid,gid=5,mode=0620 0 0
none /dev/shm tmpfs rw,nosuid,nodev 0 0
none /var/run tmpfs rw,nosuid,mode=0755 0 0
none /var/lock tmpfs rw,noexec,nosuid,nodev 0 0
none /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
none /var/lib/ureadahead/debugfs debugfs rw,relatime 0 0
/dev/sda5 /home ext4 rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/wim/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=wim 0 0
[COLOR=Red][B]/dev/sdb1 /media/DISK_IMG vfat rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,flush 0 0
[/B][/COLOR]


WHen i run that command , whatever is in red i dint get that

---

### Post by shamz_71 on 2011-07-08
> **Wim Sturkenboom said:**
> 
If it's not yet mounted, you can mount it on e.g. /mnt
[code]
wim@ubuntuserver:~$ **sudo mount /dev/sdb1 /mnt**
wim@ubuntuserver:~$ **ls -l /mnt**
total 32
drwx------ 2 wim wim 16384 2010-12-20 15:27 Tokina_EL28_20101220
drwx------ 2 wim wim 16384 2011-01-18 17:30 vivitar_55macro_20101229




farooq@KhalidTank:~$  sudo mount /dev/sdb1 /mnt
[sudo] password for farooq: 
mount: you must specify the filesystem type

---

### Post by Wim Sturkenboom on 2011-07-08
> **shamz_71 said:**
> WHen i run that command , whatever is in red i dint get thatOK, as a result, it will also not show on the desktop.

---

### Post by Wim Sturkenboom on 2011-07-08
> **shamz_71 said:**
> farooq@KhalidTank:~$  sudo mount /dev/sdb1 /mnt
[sudo] password for farooq: 
mount: you must specify the filesystem typeOK, how is it formatted? FAT32 or NTFS or ...

For fat32, try 
```

sudo mount -t vfat /dev/sdb1 /mnt

```
Don't know what to use for ntfs

---

### Post by shamz_71 on 2011-07-09
> **Wim Sturkenboom said:**
> OK, how is it formatted? FAT32 or NTFS or ...

For fat32, try 
```

sudo mount -t vfat /dev/sdb1 /mnt

```Don't know what to use for ntfs

i think its ntfs

---

### Post by Wim Sturkenboom on 2011-07-10
You should be able to find that out from within Windows.

You can try to replace vfat by *ntfs* or *ntfs-3g* if it is ntfs; see if you can find some recent info on the web.

In another recent thread it was mentioned that windows is easier on a 'corrupted' ntfs disk than Linux. If that is true AND if your disk is corrupted in some way, I would first try to defrag it in windows (if that is possible). If that does not solve the issue, a format is the only way I see.

And after that I'm out of options.

---

