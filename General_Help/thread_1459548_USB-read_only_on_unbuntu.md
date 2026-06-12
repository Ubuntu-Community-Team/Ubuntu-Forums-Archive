---
title: "USB-read only on unbuntu"
date: 2010-04-21
forum: General Help
---

### Post by Matthewx on 2010-04-21
Hi

My friend put ubuntu on my pc last year as i had problems with spyware, however I brought a new pc the other day with windows 7 as I have grew tired of ubuntu, this may be due to the fact im crap with computers.
Another friend gave me his usb key so I can take my files of my old pc and put them onto my new pc, however I plugged the usb into the pc and it won't let me put any of my files on the key, it says ''this destination is read only'', I tried changing the permission in properties but nothing will work.
Any help would be greatly appreciated


Cheers

---

### Post by thomasaaron on 2010-04-21
Run this command from a terminal...

sudo apt-get install gparted

...and then go to System > Administration > Partition Editor (or it may be System > Administration > GParted) and format the drive to ext3. Then try putting your files on it.

---

### Post by dannyboy79 on 2010-04-21
> **thomasaaron said:**
> Run this command from a terminal...

sudo apt-get install gparted

...and then go to System > Administration > Partition Editor (or it may be System > Administration > GParted) and format the drive to ext3. Then try putting your files on it.
DONT DO THIS UNLESS YOU'RE PREPARED TO INSTALL [http://www.fs-driver.org/](http://www.fs-driver.org/) IN YOUR WINDOWS 7 COMPUTER TO BE ABLE TO ACCESS THE FILES ON THE USB STICK. I can try to assist you in figuring out why your usb stick is being auto mounted read-only but I need some info.
after you insert the stick, enter this command in a terminal window and tell me what it spits out
```
tail dmesg
```
also, this command
```
mount
```
finally command
```
sudo fdisk -l
``` (using sudo can be dangerous so I'll tell you what this command is doing. it is accessing a hardware layer to determine what hard drives are seen by the OS and also what partitions are within those hard drives. you must use sudo (root priveleges) to access the hardware layer.

Post all output back here and I'll try to help. also, what version of ubuntu are you running. and what kernel. to find out kernel issue this
```
uname -r
```

---

