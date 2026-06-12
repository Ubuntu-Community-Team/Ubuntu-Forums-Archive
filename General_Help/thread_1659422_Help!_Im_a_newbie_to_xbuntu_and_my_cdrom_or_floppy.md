---
title: "Help! Im a newbie to xbuntu and my cdrom or floppy disk dont seem to auto-mount"
date: 2011-01-04
forum: General Help
---

### Post by leohopkins1 on 2011-01-04
Hi people,

I have recently installed Xbuntu on my old laptop (An IBM iSeries 2621) - yes its an old piece of kit with a USB 1.0 port, a cd-drive and an internal floppy.

My problem is that even though removable media are set to auto-mount in the settings; when I put a floppy disk in, or a CD-ROM, they do not auto-mount so I cant access the disks :(

(the laptop does not have wireless (or even an rj45 port!! - it only has an internal 56k modem) - hence why I REALLY need to get the CD-ROM working and recognised by Xbuntu as I have burned some packages that id like to install to CD-ROM. (a working floppy would definately be a bonus as id like to save my documents there)

Any ideas people?

dont forget - im a newbie ! - please be gentle !!

thanks

---

### Post by damphoud on 2011-01-04
With regards to the CD drive, have you tried other CDs, as the drive in general may not be able to pickup the burnt CD (although you probably used such CDs to install the OS)?

Also, could you give the output of: ```
sudo lshw -html >> Desktop/config.html
```

Within the above config file (which shows your hardware information, and is saved to your desktop in html format as config.htm), try to find the device with 'cdrom' and/or 'floppy' -- the output is way to huge for you to copy it all, and I'm not sure if you can have lshw be specific to a certain ID (well -class wasn't working :().

---

### Post by leohopkins1 on 2011-01-04
> **damphoud said:**
> With regards to the CD drive, have you tried other CDs, as the drive in general may not be able to pickup the burnt CD (although you probably used such CDs to install the OS)?

Also, could you give the output of: ```
sudo lshw -html >> Desktop/config.html
```Within the above config file (which shows your hardware information, and is saved to your desktop in html format as config.htm), try to find the device with 'cdrom' and/or 'floppy' -- the output is way to huge for you to copy it all, and I'm not sure if you can have lshw be specific to a certain ID (well -class wasn't working :().


Hi Thanks :-)

The output of that is:

CDROM:...
id: cdrom
description: DVD reader
product: DVD-ROM SD-C2303
vendor: Toshiba
physical id: 1
bus info: scsi@1.0.0.0
logical name: /dev/cdrom
logical name: /dev/dvd
logical name: /dev/scd0
logical name: /dev/sr0
version: 1217
capabilities: removable audio dvd
configuration: ansiversion = 5
                     status       = ready


id:  medium
physical id: 0
logical name: /dev/cdrom

* no floppy drive is mentioned in the output.  I have tried a couple of CD's (and yes, you're right, I installed from a burned CD anyway.

Both the floppy and CD worked with the installation of XP I had on before.

Any help would be much appreciated. :)

thanks :)

---

### Post by leohopkins1 on 2011-01-05
Hi,  in addition I have typed in the following commands:

wodim --devices

gives me:

-------------------------------------------------------------------------------
0 dev=' /dev/scd0'      rwrw--   : 'TOSHIBA'  'DVD-ROM SD-C2302'
-------------------------------------------------------------------------------

I then did:

sudo mkdir /media/cdrom0
 (okay so far)

then........

sudo mount -t iso9660 /dev/sdc0  /media/cdrom0/

which gives:

mount:   special device /dev/sdc0 does not exist

---

### Post by damphoud on 2011-01-05
> **leohopkins1 said:**
> Hi,  in addition I have typed in the following commands:

wodim --devices

gives me:

-------------------------------------------------------------------------------
0 dev=' /dev/scd0'      rwrw--   : 'TOSHIBA'  'DVD-ROM SD-C2302'
-------------------------------------------------------------------------------

I then did:

sudo mkdir /media/cdrom0
 (okay so far)

then........

sudo mount -t iso9660 /dev/sdc0  /media/cdrom0/

which gives:

mount:   special device /dev/sdc0 does not exist


Maybe you made a simple typo here, but it should have been:

```
sudo mount -t iso9660 /dev/s**cd**0 /media/cdrom0/
```

---

