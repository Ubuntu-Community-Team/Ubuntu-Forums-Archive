---
title: "How to update from Ubuntu 8.02 to 11.04?"
date: 2012-05-12
forum: General Help
---

### Post by BSG Fan on 2012-05-12
by internet, no CD_ROM.

sudo?

---

### Post by zombifier25 on 2012-05-12
Well, you can modify the lines in /etc/apt/sources.list to the version you need and then do a dist-upgrade.

But this will go wrong one way or another. Best option is to reinstall completely using a CDROM or USB drive.

---

### Post by sikander3786 on 2012-05-12
> **BSG Fan said:**
> by internet, no CD_ROM.

sudo?
It was 8.04 and not 8.02 actually. :)

If you are talking about 8.04 desktop edition, support for it has already ended and you would be no longer be able to access the repositories unless you tweak them a bit:

[http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html](http://www.tuxgarage.com/2011/01/access-repositories-on-eol-end-of-life.html)

Once you make the changes to the sources.list file, run an update:

```
sudo apt-get update
sudo apt-get upgrade
```

Then, open Update Manager and see if it is offering an upgrade to 10.04. If it is, choose to upgrade. If not, press "Alt + F2" and run:

```
update-manager -d
```

This time, hopefully, it would present an upgrade. Look closely if it is upgrading you to 10.04 or anyother version and perform the upgrade.

Once you've upgraded to 10.04, you can follow the routine procedure for upgrading to 12.04 i.e., install the updates and run Update Manager and upgrade.

But in fact, going for a clean install would be far more easy and hassle free for you. And there is no guarantee that you upgrade would succeed actually.

---

### Post by Bucky Ball on 2012-05-12
If you've no CD do the clean install with a USB dongle. As the others have said, prepare to spend a bit of time upgrading through to 12.04 (or 11.04) and the possibility of failure if you go that route. Save yourself the headache and time if you can do a clean install of 11.04 via USB. ;)

---

### Post by codingman on 2012-05-12
do you have a usb port and drive? you can install ubuntu 12.04 on it and then do live cd and get used to it.

find out you don't like unity?
go here:[http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm](http://ubuntublog.org/how-to-remove-unity-desktop-in-ubuntu-12-04.htm)

---

