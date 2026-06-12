---
title: "Unable to read DVDs, able to read CDs."
date: 2011-03-15
forum: General Help
---

### Post by Procrat on 2011-03-15
The titles says about everything. CD's are perfectly automounted.
When I insert a DVD however (I tried various DVDs), absolutely nothing happens, as if I would have inserted nothing or a blank DVD.

I already read lots of threads and nothing seems to help... Here are the outputs of a few commands that might or might not be useful. :-)

A line I added myself in fstab which appears completely useless:```
/dev/sr0    /media/dvd    auto    utf8,user,noauto,exec    0    0
``````
$ mount /dev/sr0
mount: /dev/sr0: unknown device
``````
$ sudo mount /dev/sr0 /media/dvd
mount: /dev/sr0: unknown device
``````
$ dmesg | grep -e DVD -e dvd
[    2.658008] ata3.00: ATAPI: HL-DT-STDVDRRW GSA-H30L, S755, max UDMA/33
[    2.677835] scsi 2:0:0:0: CD-ROM            HL-DT-ST DVDRRW GSA-H30L  S755 PQ: 0 ANSI: 5
[    2.683330] sr0: scsi3-mmc drive: 40x/40x writer dvd-ram cd/rw xa/form2 cdda tray
``````
$ sudo mount /dev/sr0 /media/dvd -t udf
mount: no medium found on /dev/sr0
``````
$ sudo mount /dev/sr0 /media/dvd -t iso9660
mount: no medium found on /dev/sr0
``````
$ ls -l /dev/{*cd*,*dvd*}
lrwxrwxrwx 1 root root  3 2011-03-15 23:31 /dev/cdrom2 -> sr0
lrwxrwxrwx 1 root root  3 2011-03-15 23:31 /dev/cdrw2 -> sr0
lrwxrwxrwx 1 root root  3 2011-03-15 23:31 /dev/dvd2 -> sr0
lrwxrwxrwx 1 root root  3 2011-03-15 23:31 /dev/dvdrw2 -> sr0
lrwxrwxrwx 1 root root  3 2011-03-15 23:31 /dev/scd0 -> sr0
```Part in output of `lshw` about the drive:
```
           *-cdrom
                description: DVD-RAM writer
                product: DVDRRW GSA-H30L
                vendor: HL-DT-ST
                physical id: 1
                bus info: scsi@2:0.0.0
                logical name: /dev/cdrom2
                logical name: /dev/cdrw2
                logical name: /dev/dvd2
                logical name: /dev/dvdrw2
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: S755
                serial: [HL-DT-STDVDRRW GSA-H30L S75506/12/26&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
```Any ideas? :-)

---

### Post by zvacet on 2011-03-15
Read [this.]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")

---

### Post by jerome1232 on 2011-03-15
Has this drive been able to read dvd's under another operating system? Part of me thinks the hardware is faulty since it's reporting a status of no disc when you insert a dvd.

I don't think it has to do with libdvdcss2 since you can still mount dvd's regardless, you just couldn't play them in a media player.

---

### Post by Procrat on 2011-03-16
> **zvacet said:**
> Read [this]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs")Libdvdread4 was already installed and fully updated. I ran the mentioned script, but to no avail.
Playing the DVDs in VLC or MPlayer with the option "No DVD menus", as the troubleshooting part says, doesn't work either.

> **jerome1232 said:**
> Has this drive been able to read dvd's under  another operating system? Part of me thinks the hardware is faulty since  it's reporting a status of no disc when you insert a dvd.I haven't had another OS for over a year and a half, so can't really remember, but I'm quite sure I could play DVDs.
I don't know if it's possible that a hardware problem could cause this strange issue, but if that really is the problem, is there something I could do? Say, change an option in the BIOS, or make sure the connections are correct when I open my computer? (I don't know much about the interior of my computer however...)

---

### Post by Procrat on 2011-04-02
Are there any other ideas?
This problem is not urgent though.;)

---

