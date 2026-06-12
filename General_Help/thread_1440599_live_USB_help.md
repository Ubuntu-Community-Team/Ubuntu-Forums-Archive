---
title: "live USB help"
date: 2010-03-27
forum: General Help
---

### Post by ferret man on 2010-03-27
I would like to make a live USB of Ubuntu that I can carry with me to school (as the computers there use Windows) so I can do my work on a computer-system I am comfortable with. I have a 1 GB flash drive and an 8 GB flash drive. Can someone help me and describe what to do?

---

### Post by l.billon on 2010-03-27
Hi!
Use the [usb-creator]("https://help.ubuntu.com/community/Installation/FromUSBStick#From%20Linux") software!

---

### Post by ferret man on 2010-03-27
I want something that I can save my work to.

---

### Post by l.billon on 2010-03-27
Actually it does, 
When formatting the usb drive with the usb creator,it will ask you if you want it to store your files too, you'll just have to specify the size of the document's partition.

---

### Post by sille777 on 2010-03-27
> **ferret man said:**
> I want something that I can save my work to.

Try this How TO: [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

Its what i did for my 8GB Flash drive.

You can save work and settings.

---

### Post by mr clark25 on 2010-03-27
i would use the 8GB flash drive. the system files will use ~75% of the space if you use the 1 GB, and thats before you install any extras.

---

### Post by l.billon on 2010-03-27
> **sille777 said:**
> Try this How TO: [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

Its what i did for my 8GB Flash drive.

You can save work and settings.

IMHO, the usb-creator method is simpler, I dit it several times and always worked like a charm.

---

### Post by Directive 4 on 2010-03-27
> **sille777 said:**
> Try this How TO: [http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)

Its what i did for my 8GB Flash drive.

You can save work and settings.


this is what i did on my 4gb usb, works like a charm.

fullyfunctional os on a stick, 

imo i wouldn't worry about making a liveusb, seems a bit pointless to me when this works great. 

for example, if you wanted to install ubuntu on your computers hard drive, would you make a live hard drive with a seperate partition to store files?


1 point, tho, i don't think you will need to do the second set of instructions, (1-12) i didn't, and mine works fine

---

### Post by sille777 on 2010-03-27
> **Directive 4 said:**
> ....

1 point, tho, i don't think you will need to do the second set of instructions, (1-12) i didn't, and mine works fine

Yeah, I didn't need to follow the second set of instructions either.

One laptop I have does not allow for usb boot, but the bios saw it as a HDD so I just had to tell the bios to boot the (usb)hdd.

It works great!!  It is a tad slow compared to running on a traditional install on an internal hdd.

---

### Post by C.S.Cameron on 2010-03-28
Both methods have their advantages and disadvantages.
With the persistent method, (usb-creator, Unetbootin), you will quickly fill your drive if you try an update and an upgrade won't upgrade your kernel. Also your persistence is limited to 4GB as it is stored in a FAT32 file. For more persistence you need to make an ext2 or ext3 partition named casper-rw.
A full install takes more space than a persistent one and might not work on all computers if you start adding restricted drivers, (ie Nvidia or ATI). 
If you want to use your flash drive to copy stuff from a Windows machine you need to use manual partitioning with the full install and leave your first partition as FAT32.
With the persistent install it is already FAT32 and windows can access the drive, but you need to go to filesystem/cdrom to access these files when booted from the drive.

---

### Post by Directive 4 on 2010-03-28
or, just install to the usb leaving it's file system as fat 32, 

this will work with windows/mac computers to transfer files etc., 

no need to make 2 partitions,

just use the method that you would use to install to your hard drive, 

remembering the bootloader and to retain fat32.

---

### Post by ferret man on 2010-03-28
After much thinking, I have come to the conclusion that the best solution is using the USB-Creator. Allow me to explain. By creating a "Live USB" I am freeing up space by using compressed filesystems. Now, I selected the option 'store on disk' with all of the remaining memory because I need to be able to save things onto it. Then I booted up, and I went to Synaptic and removed the package that allows you to install the OS. This 'neutered' the system, so to speak, thus making it impossible to install on another system. Now it is not actually a live USB, but more of a 'compressed OS' as I have chosen to call it. This allows me to retain a compressed file system with a lot of free space that I can use as a portable OS. Please tell me your feelings on this method, that would greatly help.

---

### Post by C.S.Cameron on 2010-03-28
The file where the persistence is saved is named casper-rw, it's maximum size is 4 GB. I would not try to use all remaining space even if you could as it can only be accessed when booted from the device.
If you make it 4GB, it leaves about 3GB of storage space on an 8GB drive.
If you write to this space on a windows machine you you need to go to filesystem/cdrom to access these files when booted from the drive.

---

### Post by ferret man on 2010-03-28
How would I go about opening the casper-rw?

---

### Post by ferret man on 2010-03-28
wait.. can I reformat the USB drive to ext3 and still run it after I re-paste the files?

---

### Post by C.S.Cameron on 2010-03-29
this is how I set up a persistent install:

Boot Live CD.
Plug in flash drive.
Start Partition Editor
Create 1 GB FAT32 partition, (on the left side of the bar). (size is optional)
Create a 1.5 GB ext3 partition to the right of this, labeled it "casper-rw". (ext2 and ext4 also work).
Create a partition in the remaining space and label it "home-rw". (optional, creates a separate home partition)
Close Partition Editor.
Un-mount and re-mount flash drive.
Start "Create a live usb startup disk", (usb-creator).
Select "Discard on shutdown".
Press "Make Startup Disk.
When usb-creator finishes, run "gksu nautilus"
Select disk / syslinux / text.cfg and added "persistent" as shown below:
append  noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

I'm not sure if you can open a casper-rw file.
I understand that a persistent install only works with a FAT32 FS and a Full install will work with anything but FAT32.

---

