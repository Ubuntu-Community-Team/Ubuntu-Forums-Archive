---
title: "Need to install fedora on my laptop with no CD/DVD"
date: 2010-08-31
forum: General Help
---

### Post by Clubjob on 2010-08-31
Anyone know how to get Fedora on USB Flasdrive in ubuntu cause i am tired of the missing documentations for everything i try and do in this OS.

Make commands dont work at all, lack of documentations for how to work with Unetbooting and just about everything else, cant do a thing other then waste power cause it stalls each and everytime, so frusterating that no one seems to care if new/novise linux users cant even get help to do the most simple things in linux.

Ubuntu has to be the biggest dissapointment i have ever incountered and i wont stay, if you guys cant(will not) help me then it only shows how much more ubuntu is a disaster in how userfriendly and community friendly ubuntu really is.

---

### Post by pmlxuser on 2010-08-31
i would use the dd command, use with care

sudo dd if=isoimage of=flsh_drive (usulaly inf the form /dev/sda)

as i said care just do $ dd --help to get more info on this wonderful but dangerous command

---

### Post by DemonBob on 2010-08-31
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

```
sudo apt-get install unetbootin
```

FLASH drive needs to be formatted in FAT32

---

### Post by Clubjob on 2010-08-31
> **DemonBob said:**
> [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

```
sudo apt-get install unetbootin
```

FLASH drive needs to be formatted in FAT32

That program dont work, you can put OS/iso on the USB drive but it cant boot, it just says missing operationsystem.

Geezh, none of that work.

Now i have to drive over to my buddy with a windows computer and do it there.

Thanks for nothing ubuntu.

---

### Post by mickwombat on 2010-08-31
Without testing this, how about formatting the USB in FAT32 *and* flagging it as bootable.  Don't just copy the iso, but mount it and copy all the files, including hidden ones, across to the USB.  Try to boot off it then.
Hope it works
;-)

---

### Post by Dayofswords on 2010-08-31
> **Clubjob said:**
> That program dont work, you can put OS/iso on the USB drive but it cant boot, it just says missing operationsystem.

Geezh, none of that work.

Now i have to drive over to my buddy with a windows computer and do it there.

Thanks for nothing ubuntu.
harsh much?

and it just sounds like you havent make it boot to usb and is going to the hdd first...

---

