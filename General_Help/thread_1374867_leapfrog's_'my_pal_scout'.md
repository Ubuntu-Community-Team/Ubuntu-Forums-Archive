---
title: "leapfrog's 'my pal scout'"
date: 2010-01-07
forum: General Help
---

### Post by tje210 on 2010-01-07
so i got this toy that you can load stuff on... but the only stuff is a very limited list of songs and words.  i'm trying to get to the drive inside the toy, but i'm quite the n00b to this kind of thing.  i did a little research, so this is the info i have:

first off, this is the result in /var/log/messages when i plug Scout in.
ubuntuMBP kernel: [  216.820237] usb 3-2: new full speed USB device using uhci_hcd and address 5
ubuntuMBP kernel: [  216.979863] usb 3-2: configuration #1 chosen from 1 choice
ubuntuMBP kernel: [  216.990080] scsi5 : SCSI emulation for USB Mass Storage devices
ubuntuMBP kernel: [  221.994703] scsi 5:0:0:0: Direct-Access     Leapfrog My Pal Scout     1.00 PQ: 0 ANSI: 0
ubuntuMBP kernel: [  221.995673] sd 5:0:0:0: Attached scsi generic sg2 type 0
ubuntuMBP kernel: [  222.006574] sd 5:0:0:0: [sdb] Attached SCSI disk

that told me to try to treat it like a SCSI disk (which i have ~0 experience with).  the disk doesn't show up on my desktop or in Places > Computer.  and now i have no idea how to proceed.  any ideas/suggestions would be greatly appreciated.

i do realize that once i get in, the files that are usable by the toy may be in a format i can't supply, or something else may be going on... but i figure i'll just cross that bridge when i come to it.

---

### Post by 3rdalbum on 2010-01-07
Some sorts of devices were around in SCSI first, before USB became popular; so when the USB versions came out, they still communicated with the computer as though they were SCSI devices. In short, don't worry about "SCSI".

If this device has not mounted on your desktop, you will need to mount it yourself. Use this command:

```
sudo fdisk -l
```

to work out the device file path of the Leapfrog's filesystem (it will be something like "/dev/sdc1"). Once you know this, you can run the following commands:

```
sudo mkdir /media/leapfrog
sudo chmod a+rw /media/leapfrog
sudo mount /dev/sdc1 /media/leapfrog
```

Hopefully this should mount it, and you'll get a desktop icon. You won't be able to unmount it from Gnome - instead you can do:

```
sudo umount /media/leapfrog
```

---

### Post by tje210 on 2010-01-11
i appreciate your assistance!  fdisk isn't quite the command to use, but it got me started thinking.

so yeah, did fdisk -l, that just showed me the partitions on my HDD.  checked my var/log/messages to make sure it had been attached, it indeed had.  did the 'lsusb' command... that gave me 

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 05ac:0220 Apple, Inc. Aluminum Keyboard
Bus 001 Device 004: ID 152d:2338 JMicron Technology Corp. / JMicron USA Technology Corp. JM20337 Hi-Speed USB to SATA & PATA Combo Bridge
Bus 001 Device 003: ID 05ac:1006 Apple, Inc. Hub in Aluminum Keyboard
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 003: ID 0f63:0d00  
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

basically, all of those devices are accounted for; none of them are Scout.

so i thought to myself, i wonder if there's an lsscsi command.  turns out there is.  did the sudo apt-get thing, ran lsscsi.  Bingo-ish!

[4:0:0:0]    disk    ATA      WDC WD200BB-75CL 05.0  /dev/sda
[6:0:0:0]    disk                                    /dev/sdb
[10:0:0:0]   disk    Leapfrog My Pal Scout     1.00  /dev/sdc

ok, so that actually gets us back to the beginning, which i didnt document... i already mkdir'ed media/leapfrog; i chmod'd it, then without knowing the name of the device, tried mounting sdc1, sdc0, and finally plain old sdc.  sdc0/1 both said they didn't exist.  sdc, however, just said i needed to specify a filesystem type.  i wasn't sure exactly what that meant, now i know.  

so awesome.  now to find what filesystem to use.  did a google search, found something about a file -s command?  checked up on it... here's the progression

$ file /dev/sdc
/dev/sdc block special
$ file -s /dev/sdc
/dev/sdc: no read permission (curses!  foiled again!)
$ sudo chmod 755 /dev/sdc
$ file -s /dev/sdc
/dev/sdc: empty

Drat!  The thing plays, so it's not empty.  did some more looking around, did a /cat/fstab, didn't tell me anything cool.  saw something about fsck -N /dev/sdc ... that returns

fsck from util-linux-ng 2.16
[sbin/fsck.ext2 (1) -- /dev/sdc] fsck.ext2 /dev/sdc

Hmm so this might mean that it's ext2.  now to try mounting it...

$ sudo mount -t ext2 /dev/sdc /media/leapfrog
mount: wrong fs type, bad option, bad superblock on /dev/sdc,
       missing codepage or helper program, or other error
       (could this be the IDE device where you in fact use
       ide-scsi so that sr0 or sda or so is needed?)
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Hrm.  I think this is about the end of the road for right now.  I think a clue is that 'block special' message.  It's special in some way, and i have no idea what way that is!  did a quick wiki on 'block special', didn't really give me anything useful.

oh yeah, and after all these things i did, did a quick ls /media/leapfrog, and of course it returned nothing.

---

### Post by bluesterror on 2011-07-12
My recent blog posting on the topic should shed some light:

[http://bobcopeland.com/blog/2011/07/my-pal-scsi/](http://bobcopeland.com/blog/2011/07/my-pal-scsi/)

However, you don't really have to hack the interface to load your own stuff on the device; you just need a web proxy that intercepts requests to the http servers made by the windows-based connect software.  But you would need to figure out what format those files are in.

---

### Post by locutus42 on 2011-12-09
> **bluesterror said:**
> My recent blog posting on the topic should shed some light:

[http://bobcopeland.com/blog/2011/07/my-pal-scsi/](http://bobcopeland.com/blog/2011/07/my-pal-scsi/)

However, you don't really have to hack the interface to load your own stuff on the device; you just need a web proxy that intercepts requests to the http servers made by the windows-based connect software.  But you would need to figure out what format those files are in.

I just ran the software in a VM( must run XP - not 98 ) and at least for the music it seems to download the files from the web first before syncing the files onto the device. For some reason they even have it set up so the files don't go on the device until the next time you connect.

Using their software you can see they really want to create a portal for all kinds of software for the devices and online games, info, etc. It's no wonder there's not a simple update facility available, they've created their own Leap World( thinking Walley World here ).

---

