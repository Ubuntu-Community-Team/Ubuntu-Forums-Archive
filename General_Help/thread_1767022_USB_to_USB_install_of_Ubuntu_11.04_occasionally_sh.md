---
title: "USB to USB install of Ubuntu 11.04 occasionally shows input/output errors?"
date: 2011-05-25
forum: General Help
---

### Post by darkaspitch on 2011-05-25
I have about 7 Patriot XT USB drives (~30mb/s read/write) that I use to install ubuntu with and onto.

I am using unetbootin on windows to create the usb installer.

Occasionally I will receive errors part way through installation. Usually error code 5, and input/output error.

It warns me that perhaps my cd was burned too quickly (although I am installing from USB) or that the environment might be too hot. (It's about 30 degrees celcius in there right now).

I have managed to install ubuntu to/from these same usb drives in the past.

Anybody know what could be causing this?

Here is my process...
 - insert usb drive of 8GB into windows machine and format it with fat32
 - create a bootable ubuntu live install on the 8GB usb and safely remove the drive
 - insert the 8GB usb and a blank 16GB usb into the target install machine
 - enter the default unetbootin setup
 - install ubuntu to the 16gb usb

---

### Post by novinick on 2011-05-25
try this:

There is option in unetbootin to temporary install on first hard drive , 
it is c: or / , and then boot from it. 
There will be new option in grub or in vista boot menu called 'unetbootin' 

and then insert other usb stick , which is 16GB and install on it . 
That way will be no usb conflicts.
:guitar:

---

### Post by novinick on 2011-05-25
what is exact meaning of 'ocasional' ?

it is also probable that one or two of your flash drives are got broken with time
and normal usage.

---

### Post by darkaspitch on 2011-05-25
> **novinick said:**
> try this:

There is option in unetbootin to temporary install on first hard drive , 
it is c: or / , and then boot from it. 
There will be new option in grub or in vista boot menu called 'unetbootin' 

and then insert other usb stick , which is 16GB and install on it . 
That way will be no usb conflicts.
:guitar:

I'm not 100% sure what you're saying here..?

I do not think you can install onto the drive that you have the install files loaded onto. Can you elaborate?

---

### Post by darkaspitch on 2011-05-25
> **novinick said:**
> what is exact meaning of 'ocasional' ?

it is also probable that one or two of your flash drives are got broken with time
and normal usage.

By occasional, I mean all the time :S

It never used to happen, now it happens with every install it seems.

I just purchased these drives a few weeks ago and they claim to have no errors present when I check them.

Perhaps it actually is the temperatures in the room?

Trying another brand now...

---

### Post by novinick on 2011-05-25
okay let's re-check procedure

> Here is my process...
 - insert usb drive of 8GB into windows machine and format it with fat32
 - create a bootable ubuntu live install on the 8GB usb and safely remove the drive
 - insert the 8GB usb and a blank 16GB usb into the target install machine
 **- enter the default unetbootin setup**
 - install ubuntu to the 16gb usb


by words 'default unetbootin setup' , did you started live usb instaler , from menu ?
or usual hard disk installer ? or another copy of unetbootin?

this is unetbootin screen as you know allready
[http://sourceforge.net/dbimage.php?id=294733](http://sourceforge.net/dbimage.php?id=294733)
this is live usb instaler ,his funcionality differs,creates persistency
[http://en.wikipedia.org/wiki/File:Make_Startup_Disk_001.png](http://en.wikipedia.org/wiki/File:Make_Startup_Disk_001.png)
Do you have persistancy?

Did you formated 16Gb drives as fat32 or as ext2-ext3-ext4 , perhaps is ext2 suitable for flash then ext3 ext4,
if not used fat32. Usualy fat32 does the trick for live instals

it would be usefull , after you get those errors
to post dmesg , from booted 8GB drive
(while this operation is in progres)
```

dmesg

``` 

so botom line is to create 16Gig stick, which is live, with persistancy ?
may be ways to shorten procedure, by using some of  pendrivelinux setup methods
(direct from windows)
ubuntu should adjust it self to target mashines automaticaly after first boot


also is sugested for cow device to be mounted as read only
or using noatime parameter ater first boot , in /etc/fstab ,for 16 gig drives
this counteracts usb flash cells wearing off
```

....-o noatime...

```
see manuall how to add

---

### Post by novinick on 2011-05-25
as i re-read ubutnu wiki
 [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 

there is build of live usb creator , for windows ? called **usb-creator.exe** so you may shorten a few steps (if it works for you)
to put direct to 16 GB drives without intermediary 8Gig drive

usually it is inside .iso image :popcorn:

> **From Windows**

 Versions  of Ubuntu other than Ubuntu 9.10 (Karmic Koala) include a file called  usb-creator.exe in the CD image. You need to run this program, so you  need to copy it out of the CD image.  To do so, you can burn the Ubuntu  ISO file to a disk, or you can use a Windows utility such as [Virtual Clone Drive]("http://www.slysoft.com/en/virtual-clonedrive.html") to access the .iso file's contents.  You can also use [7Zip]("http://www.7-zip.org/") to extract the ISO so you can work with the files inside. 
This process is described in detail in a video on [this website.]("http://403forbidden.dyndns.org/?page_id=316") 
Once  you have usb-creator.exe, run it and follow the same steps as described  for Linux (point it at your .iso file or your Ubuntu CD-ROM, point it  at your USB flash drive, make sure you have the right device selected,  then "Make Startup Disk").
*Notes* 

[LIST]
[*]Instead of usb-creator.exe you can use Unetbootin to create a bootable USB drive. [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
[*]You  won't be able to select the USB drive if it wasn't formatted in a way  that Windows can see it.  You may have to format it using Windows  Explorer in order for it to show up in a creator tool.
[/LIST]

 

---

