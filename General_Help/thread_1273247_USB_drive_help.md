---
title: "USB drive help"
date: 2009-09-23
forum: General Help
---

### Post by Alcar on 2009-09-23
Hello guys, Ive just installed ubuntu 9.04, Im new at this so go easy on me please :)
I tryed to use my usb drive, I want to copy a movie but it said I couldnt because there was no free space (even though I had erased all data previosly), so I opened a terminal and this is what I did: (Unmounted the drive first)

sudo mkfs.ext3 /dev/sdc

then

sudo e2label /dev/sdac usb-pen

sudo mkfs.vfat /dev/sdc

Everything seemed to be okay but now the device wont work at all, everytime i try to copy the movie it says I dont have permissi'on to do it. I need to use this drive in linux and windows, can you do this?

---

### Post by marcopalla on 2009-09-23
only a possibility, but you could try:

[FONT=Arial][SIZE=2]System - Administration - Users and Groups[/SIZE][/FONT][FONT=georgia][FONT=Arial][SIZE=2]
Click on your user name[/SIZE][/FONT][/FONT]
[FONT=georgia][FONT=Arial][SIZE=2]Click on the button "Unlock"[/SIZE][/FONT][/FONT]
[FONT=georgia][SIZE=4][FONT=Arial][SIZE=2]Properties button - tab User Privileges and make sure that every category is ticked.[/SIZE][/FONT]
[/SIZE][/FONT]

---

### Post by nothingspecial on 2009-09-23
Well ,first you need to get the syntax correct. Also do you want the pen drive to be fat32.

As you are new to this I sugest using gparted to reformat the drive.
```

sudo apt-get install gparted
```

While we`re here, it should be
```

sudo mkfs.vfat /dev/sdc1
```

or ```
sudo mkfs -t vfat /dev/sdc1
```

but gparted would be easier.

---

### Post by nothingspecial on 2009-09-23
Also you need to own the device. Assuming it it mounted at /media/usb-pen
```

sudo chown -R username:username /media/pen-drive/
```

---

### Post by Alcar on 2009-09-23
Thanks guys, this is what I get

allan@allan:~$ sudo mkfs.vfat /dev/sdc
mkfs.vfat 3.0.1 (23 Nov 2008)
mkfs.vfat: Device partition expected, not making filesystem on entire device '/dev/sdc' (use -I to override)
allan@allan:~$ sudo mkfs -t vfat /dev/sdc
mkfs.vfat 3.0.1 (23 Nov 2008)
mkfs.vfat: Device partition expected, not making filesystem on entire device '/dev/sdc' (use -I to override)
allan@allan:~$ sudo mkfs.vfat /dev/sdc

---

### Post by trundlenut on 2009-09-23
you need to create a partition to hold the file system. sdc is the device, sdc1 would be the first partition on the device (could be the whole thing), so you need to use something like gparted to create the partition and then add the file system.

---

### Post by Alcar on 2009-09-23
> **trundlenut said:**
> you need to create a partition to hold the file system. sdc is the device, sdc1 would be the first partition on the device (could be the whole thing), so you need to use something like gparted to create the partition and then add the file system.

I dont know how to do a partition in the first place :P IM really lost in here.

---

### Post by trundlenut on 2009-09-23
install gparted and use it to create a primary partition on the drive.  It's quite straightforward to use.  No need to use the CLI then.

---

### Post by Alcar on 2009-09-23
> **trundlenut said:**
> install gparted and use it to create a primary partition on the drive.  It's quite straightforward to use.  No need to use the CLI then.
 
I already installed gparted, how do I use it?

---

### Post by theozzlives on 2009-09-23
> **Alcar said:**
> I dont know how to do a partition in the first place :P IM really lost in here.

You're trying to format from the command line and don't know how to create a partition? Just use gparted, it's easy. Look in System > Administration > Partition Editor. If you don't have it do:
```
sudo apt-get install gparted
```
then look again, it'll be there. You'll wanna select the Gparted menu and Devices, select SDC3.

---

### Post by Alcar on 2009-09-23
OKay, I used Gparted and it created a fat32 partition... but now it says I cant mount the pen drive.

---

### Post by trundlenut on 2009-09-23
> **Alcar said:**
> OKay, I used Gparted and it created a fat32 partition... but now it says I cant mount the pen drive.

Did you create the partition (should be sdc1) and then create a fat32 file system on that partition?

What happens if you unplug it and then plug it back in?

---

### Post by theozzlives on 2009-09-23
> **Alcar said:**
> OKay, I used Gparted and it created a fat32 partition... but now it says I cant mount the pen drive.

Did you take the drive out and back in?

---

### Post by Alcar on 2009-09-23
> **theozzlives said:**
> Did you take the drive out and back in?

Yes, that did the trick :P

THank all of you guys for helping me out.

Allan.

---

