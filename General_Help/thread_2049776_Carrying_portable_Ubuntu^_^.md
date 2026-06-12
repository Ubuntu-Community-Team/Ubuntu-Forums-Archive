---
title: "Carrying portable Ubuntu^_^"
date: 2012-08-29
forum: General Help
---

### Post by Debash on 2012-08-29
I had ubuntu installed on my home desktop and windows on my laptop. Now, I have joined college and left Ubuntu at home. I missed it so i downloaded an ISO file and burnt it on an USB. I was wondering if i could modify the content on the USB. For instance, if i want to play media files, and i install some codecs, will they be stored on the USB? If not how can i add those codecs to the USB, similarly gcc buld tools, skype and anything else i would like to add to the USB?
Thank You in advace to all who will reply.

---

### Post by mastablasta on 2012-08-29
if you use persistance during liveUSB creating you can add codes and such into that casper file. casper file has a limited size i believe. 
 
anothe roption is to install the whole OS on USB key. for that you will needa t least 8GB usb key.

---

### Post by ajgreeny on 2012-08-29
The maximum size of the persistent casper file is 4GB because the USB for a live system is fat32.

---

### Post by C.S.Cameron on 2012-08-29
You can also use persistent partitions of unlimited size:


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
Select disk / syslinux / text.cfg and add "**persistent**" as shown below:
append  noprompt cdrom-detect/try-usb=true **persistent** file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash --
Shutdown, remove CD, reboot.
You are persistent.

---

### Post by oldfred on 2012-08-29
I post this a lot from C.S.Cameron:

Pros & cons of persistent install over direct install to flashdrives - C.S.Cameron
[http://ubuntuforums.org/showthread.php?t=1655412](http://ubuntuforums.org/showthread.php?t=1655412)

---

### Post by Debash on 2012-09-04
So what i have on my pendrive is a persistent partition and for my needs i should do a full install to the pendrive? my pendrive is only of 2 Gb...so i should get a 4gb pendrive? and how to do full install? i used netbootin.

---

### Post by black veils on 2012-09-04
no, what you have is a regular live flash drive. what you want is a persistent live flash drive. 

use this to create it:
startup disk creator (usb-creator-gtk)

should already be installed.

if you have a 6gb flash drive for instance, the tool will be used to add the iso, then there will be a max of 4gb for anything you save onto the flash drive when having the system booted. if you create/download files, or configure the system, it will be stored in that 4gb persistence (or smaller, depending on what size you choose).

---

### Post by Debash on 2012-09-12
Thanks, that cleared it up. But Can i do a persistant install in my 2GB pendrive?

---

### Post by black veils on 2012-09-13
you should be able to, just make the allocated space small enough. an alternative to using the previous application, is to use: unetbootin

---

### Post by C.S.Cameron on 2012-09-13
A basic Live install of Ubuntu takes about 800MB, This leaves about 1.2GB for persistence on a 2GB flash drive.

You probably don't need persistent partitions as I've outlined above, they are most useful for drives above 8GB.

---

### Post by Debash on 2012-09-25
THANKS. I successfully completed my persistent install yesterday using startup-creator-gtk.

---

### Post by Debash on 2012-09-25
I also found another method > 


go to any ubuntu install, type df -h in the terminal to view all the drives and select USB drive.
sudo umount /dev/sdx to unmount the drive.
sudo mkfs.ext3 -b 4096 -L casper-cow /dev/sdx to make the filesystem.
Now insert LiveCD and press F4 to go to a commad line mode and give a space and type persistent and press enter and it should be done.

---

### Post by C.S.Cameron on 2012-09-26
> **Debash said:**
> I also found another method > 


go to any ubuntu install, type df -h in the terminal to view all the drives and select USB drive.
sudo umount /dev/sdx to unmount the drive.
sudo mkfs.ext3 -b 4096 -L casper-cow /dev/sdx to make the filesystem.
Now insert LiveCD and press F4 to go to a commad line mode and give a space and type persistent and press enter and it should be done.


I understand that casper-cow has not worked for persistence since about 7.04.

---

### Post by Debash on 2012-09-28
Ok. So thats why I was not able to follow that method.

One last doubt :biggrin: Now my ubuntu installation by default boots into the install option and not into try without Installing option. Can i change the default behaviour in my persistent install?

---

### Post by C.S.Cameron on 2012-09-28
[http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit?rq=1](http://askubuntu.com/questions/47522/how-to-bypass-try-it-install-screen-when-booting-from-usb-live-session-wit?rq=1)

---

### Post by Debash on 2012-09-29
Thanks

---

