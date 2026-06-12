---
title: "DVD drive(physical) doesn't work in ubuntu!! Please help!"
date: 2011-08-03
forum: General Help
---

### Post by eveningpolestar on 2011-08-03
I am using MSI X620. I just intalled ubuntu 10.04 in it. Everything is fine except my DVD drive. The dvd drive doesn't work at all! When i press eject button ..nothing happens and there is no light blinking in the drive....when i load windows it works fine though! do i need to install drivers or something? please help!

---

### Post by UnnamedUzer on 2011-08-03
Do u see your DVD drive in BIOS?

---

### Post by eveningpolestar on 2011-08-03
yep the drive is shown in the BIOS.

---

### Post by UnnamedUzer on 2011-08-03
> **eveningpolestar said:**
> yep the drive is shown in the BIOS.

Try "lshw" in console and to find DVD in the list

---

### Post by Hatsune Miku on 2011-08-03
> **UnnamedUzer said:**
> Try "lshw" in console and to find DVD in the list

Not trying to show you up or anything

```
lshw | grep "dvd"
```

This might be a little easier

---

### Post by pqwoerituytrueiwoq on 2011-08-03
> **Hatsune Miku said:**
> Not trying to show you up or anything

```
lshw | grep "dvd"
```This might be a little easier
lshw needs sudo here and there is no reason to quote dvd since there are no spaces
```
sudo lshw | grep dvd
```
*likes your avatar*

---

### Post by eveningpolestar on 2011-08-03
i typed those codes in terminal. here is what it shows:


 *-cdrom
                description: DVD-RAM writer
                product: CDDVDW TS-U633J
                vendor: TSSTcorp
                physical id: 1
                bus info: scsi@4:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: TM00
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc

when i typed grep dvd...nothing happened...

---

### Post by pqwoerituytrueiwoq on 2011-08-03
well the dvd drive registers on ubuntu
does ```
eject /dev/sr0
``` work

also lets see what hwinfo gives you
```
sudo apt-get install hwinfo;sudo hwinfo --cdrom
```

---

### Post by eveningpolestar on 2011-08-04
> **pqwoerituytrueiwoq said:**
> well the dvd drive registers on ubuntu
does ```
eject /dev/sr0
``` work

also lets see what hwinfo gives you
```
sudo apt-get install hwinfo;sudo hwinfo --cdrom
```

the code does work but the eject button doesn't. And right clicking the cd/drive icon to eject the drive also doesn't work!!

---

### Post by Hatsune Miku on 2011-08-11
> **pqwoerituytrueiwoq said:**
> lshw needs sudo here and there is no reason to quote dvd since there are no spaces
```
sudo lshw | grep dvd
```
*likes your avatar*

ty & BUMP for a solution ;)

---

### Post by 11.04 on 2011-08-11
> **eveningpolestar said:**
> I am using MSI X620. I just intalled ubuntu 10.04 in it. Everything is fine except my DVD drive. The dvd drive doesn't work at all! When i press eject button ..nothing happens and there is no light blinking in the drive....when i load windows it works fine though! do i need to install drivers or something? please help!

Are you sure you're not booting from the Ubuntu CD?  When you boot from it, it locks the CD in the drive.

---

