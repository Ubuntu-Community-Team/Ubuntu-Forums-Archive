---
title: "How to make persistent USB from liveUSB"
date: 2010-10-12
forum: General Help
---

### Post by mastablasta on 2010-10-12
I've created a LiVeUSB drive of 10.10 with uNetbootin in a 4GB USB drive. It works very well. Now i read that to keep some settings i've made and possibly install some programmes (!?) i would need to make the USB drive persistent. 
I was checking the web but there seem to be many different types of instruction to do this. from the full install of he system to some GRUB install and certain modification...
 
I also found these instrcutions (found them in readme file here: [http://unetbootin.sourceforge.net/diskimg/](http://unetbootin.sourceforge.net/diskimg/)) that seem quite simple, however it doesn't say where exactly you are supposed to move that caper file (USB root?):
```

Go to [http://unetbootin.sourceforge.net/diskimg/](http://unetbootin.sourceforge.net/diskimg/) and download one of the files (128mb.zip, 256mb.zip, or 512mb.zip) corresponding to the amount of persistent space you want (make sure the size of the persistent disk image is smaller than the free space you have on your USB drive).
Now extract the file "casper.rw" from the zip file to your USB drive.
Now edit D:\syslinux.cfg (assuming D:\ is where your USB drive is) and add in "persistent" at the end of the line that begins with "append", and save the file, so your syslinux.cfg should look something like this:
default unetbootin
label unetbootin
        kernel /ubnkern
        append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash persistent --
For more info see [https://help.ubuntu.com/community/LiveCD/Persistence ]("https://help.ubuntu.com/community/LiveCD/Persistence")
```
 
so if i use 512MB.zip i will get 512MB pesistent space that sytsem can sue to store added data and programmes? 
 
can this file be used with Ubuntu 10.10?
 
also syslinux.cfg has more options than one, so i am guessing you need to add that persistent line to all of them?!
 
in some posts i've read that USB will get damaged fast if it is used as persistance install. is that true? is it better to have it live and then just add a folder for data on it?

---

### Post by czege on 2010-10-12
Even editing syslinux.cfg I was not able to make my uNetbootin to USB install of Ubuntu Netbook persistent. I switched from uNetbootin for the install to using pendrivelinux, which let me choose "persistent" via a checkbox when making the USB install, and now it's persistent: [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)

Paul

---

### Post by C.S.Cameron on 2010-10-12
This is how I made a Unetbootin install to flash drive persistent.
Booted Live CD, (Live USB should also work)
Plugged in target flash drive.
Started Partition Editor
Created 1GB FAT32 partition, (on the left side of the bar).
Created a 2GB ext3 partition to the right of this, labeled it "casper-rw".
Created a ext2 partition in the remaining space and labeled it "home-rw".
Closed Partition Editor.
Un-mounted and re-mounted flash drive.
Started Windows, started Unetbootin, selected Diskimage, located the iso, selected Type = USB Drive, selected correct drive letter
Pressed OK, waited 5 minutes.
When Unetbootin finished, shutdown, booted thumbdrive.
At boot menu hit Tab, then typed "(space)persistent"
Ran "gksu nauilus", opened filesystem / cdrom and then opened syslinux.cfg with text editor.
Added "persistent" as shown below:
append initrd=/ubninit file=/cdrom/preseed/ubuntu.seed boot=casper quiet splash -- persistent
Rebooted, changes were persistent.

---

### Post by mastablasta on 2010-10-13
ok but, what are those zip files then offered on uNetbutin site and why did you have to make all those separate partitions?
 
I just want to be able to install a few additional programmes (such as maybe the missing codecs) but otherwise use the disk as it is at the moment. so as live USB but with a few extras, that will stay after i take it out.
 
maybe i should just go with Mint... it would be easier. will also check the pendrivelinux...
 
also is there a degradation to USB life if i do it as you did, Cameron?

---

### Post by C.S.Cameron on 2010-10-13
The method I use allows more than 4GB persistence and the data in the home folder is not lost when upgrading versions.

For the method you are using:
You should only need to add " persistence" to the top entry in syslinux.cfg as this is the one normally used when logging in.

The casper-rw file goes into the flash drive root.

Mint persistence works the same as Ubuntu.

A flash drive is good for 10000 writes,
At 1.5MB per second it takes ~3 hours to fill a 16GB drive.
3 hours x 10000 = 30000 hours = 750 work weeks.
And many flash drives have a lifetime warranty.

---

### Post by mastablasta on 2010-10-14
now that i look slowly again at your thread that actually makes sense. however for so little (these days) data i dont' think it would be a problem to back it up to computer drive.
 
> **C.S.Cameron said:**
>  
A flash drive is good for 10000 writes,
At 1.5MB per second it takes ~3 hours to fill a 16GB drive.
3 hours x 10000 = 30000 hours = 750 work weeks.
And many flash drives have a lifetime warranty.
 
i understand that, but live system does only the reading of the USB key. with persistant drive i just want to add a few programmes that will later be read in live session. 
 
what i don't know is (and this part puzzles me) if this will mean also that live install will access (write) more times to the disk because the disk is persistant, or is this just some space that is basically alocated for any programme install or data? this information i can't find... i only found some posts where people say that USB key will get damaged faster with persistance install.
 
I totally understand that system will write down certain settings, but i do hope it want be creating any swap files and use them extensivelly, reading and writing all over the place (like windows does for example).

---

### Post by DJonsson2008 on 2010-10-14
I simply formatted the USB with gparted.

Disconnected all the other hard drives
and booted with the install disc, 

And installed Ubuntu to the USB as if 
it was another hard drive.

---

### Post by mastablasta on 2010-10-14
> **DJonsson2008 said:**
> I simply formatted the USB with gparted.
 
 
simple - yes. but also space consuming, no?

---

