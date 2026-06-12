---
title: "Iomega iConnect not mounting ext3 drive."
date: 2010-10-07
forum: General Help
---

### Post by ayenack on 2010-10-07
Hello all.

I've just bought an Iomega iConnect which mounts usb drives as network drives. The problem I'm having is that it's not mounting an ext3 partition on a drive, it mount's the NTFS and FAT but not the ext3.

If anyone has one of these and has an answer I'd be most grateful.

Thanks.

---

### Post by Merthod on 2010-10-07
I looked it up and apparently it doesn't support ext3.

---

### Post by ayenack on 2010-10-08
Apparently it does support both ext2/3 I read this on the Iomega website but can't find it now unfortunately.

Well it does support ext2 so maybe I'll format drives as that. Strange thing is I formatted a USB stick to FAT and it didn't see that either.

The story continues.

Thanks anyway.

---

### Post by blackest_knight on 2011-04-25
hi i recently bought  an iconnect and have got a little further with it

[https://sites.google.com/a/abiyo.net/www/gadgets/ext3onaniomegaiconnectwirelessdatastation](https://sites.google.com/a/abiyo.net/www/gadgets/ext3onaniomegaiconnectwirelessdatastation) 

gives details of how to build compile and insert the modules on the iconnect.

its running a version of debian. you need to download a 799meg archive from iomega to get 56 meg of kernel source use menuconfig to add in ext3 support compile it and take 3 .ko (modules) files from the fs folder which you then load into the kernel in the iconnect.

Which is as  far as i have got. The ext3 partition on my 500gb drive isn't displayed in the iconnect web interface but the iconnect knows about the  partition I think it maybe a permissions thing.

I do have root on it thou so it should be possible to go further with this
some people have got debian booting on the iconnect via a usb stick but they have opened it up to get a serial port open for the console.

I don't think i need to  go that far, my main interest is ext3  support so i can load which ever drives i want on it and  perhaps add a usb hub to increase the number of usb ports available.

I've attached a small archive which contains the 3 .ko files needed but obviously use them at your own risk. you probably would be better to build your own (but this is a lot quicker than getting the tool chain the massive archive from iomega extracting whats needed and cross compiling)

---

### Post by blackest_knight on 2011-04-25
Slight update 
after fiddling round a bit I plugged in a drive which hadn't been connected to  the iomega iconnect before. 

that works :) 
both fat and ext3 partitions recognised on that drive 

Probably doing a factory reset will reset the cache of known drives.

turns out the drive i was trying to mount was ext4 which was the problem 

doing a factory reset will wipe out the changes made in /ect/
and there is very little space in there so you can't add in ext4 modules as well or you run out of space.

---

