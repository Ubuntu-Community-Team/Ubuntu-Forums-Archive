---
title: "I really need help!"
date: 2010-04-28
forum: General Help
---

### Post by BadlyNeedHelp on 2010-04-28
Hi there, 

So I haven't installed Ubuntu yet, I am running it from the Disk.

I transferred my Pictures and some Videos from my camera to the desktop, then Ubuntu crashed so I had to turn off the Laptop and then click "Run from disk" again, doing this had let to me losing my pictures and videos that I had just transferred, and I also deleted them from my camera.

I don't know how to install .EXE files on Ubuntu either, so I can't find any recovery software that's free for Ubuntu that will let me recover my Memory Card inside my Camera so I can get my pictures and videos back.

Does anyone know how to install .EXE files on Ubuntu? I've tried WINE but can't get that installed...

Also, does anyone know any recovery software that will work on Ubuntu and is free so I can get my Pictures and Videos back.

Thanks for any help.

---

### Post by Grenage on 2010-04-28
Ok, forget about exe files for now; in fact, forget about WINE.

There are some good photorec [guides]("http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step") on Google, and those are native applications.

---

### Post by BadlyNeedHelp on 2010-04-28
Thanks for the reply, but I am very confused as to how I install the "Testdisk" im new to Ubuntu, and have no idea on how to install it.

Any help would be appreciated, I really need these photos and videos back.

---

### Post by Leppie on 2010-04-28
to install testdisk:
- open up a terminal, go to Applications > Accessories > Terminal
- type in (or copy and paste ;) ) the following command and hit enter:
```
sudo apt-get install testdisk
```- if it's prompting you with a question like if you want to continue, just confirm

to start photorec:
```
sudo photorec
```

the follow the guide Grenage linked

---

### Post by BadlyNeedHelp on 2010-04-28
Thanks, but it keeps saying this:

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk


What version do I download from the TestDisk website?


[LIST]
[*] [IMG]http://www.cgsecurity.org/os/dos.png[/IMG] [Dos/Win9x]("http://www.cgsecurity.org/testdisk-6.11.3.dos.zip")
[*] [IMG]http://www.cgsecurity.org/os/win.png[/IMG] [Windows]("http://www.cgsecurity.org/testdisk-6.11.3.win.zip")
[*] [IMG]http://www.cgsecurity.org/os/linux.png[/IMG] [Linux]("http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2"), kernel  2.6.x i386/x86_64
[*] [IMG]http://www.cgsecurity.org/os/linux.png[/IMG] [Linux]("http://www.cgsecurity.org/testdisk-6.11.3.linux24.tar.bz2"), kernel  2.4.x i386/x86_64
[*] [IMG]http://www.cgsecurity.org/os/rpm.png[/IMG] Linux [i386 RPM]("http://www.cgsecurity.org/testdisk-6.11.3-1.i386.rpm")
[*] [IMG]http://www.cgsecurity.org/os/rpm.png[/IMG] Linux [SRPM]("http://www.cgsecurity.org/testdisk-6.11.3-1.src.rpm")
[*] [IMG]http://www.cgsecurity.org/os/mac.png[/IMG] [Mac OS X]("http://www.cgsecurity.org/testdisk-6.11.3.darwin.tar.bz2")
[*] [IMG]http://www.cgsecurity.org/os/os2.png[/IMG] Non official version of [PhotoRec for OS2]("http://www.fbakan.de/photorec-os2.htm")
[*] [Source code]("http://www.cgsecurity.org/testdisk-6.11.tar.bz2") - [Patch v2 for PhotoRec]("http://www.cgsecurity.org/photorec_611_exif_bound_checking_v2.patch") adding missing boundary check in EXIF processing
[*] Documentation to download: [bz2 archive]("http://www.cgsecurity.org/testdisk-doc-6.11.tar.bz2") (2.9 MB), [zip archive]("http://www.cgsecurity.org/testdisk-doc-6.11.zip") (3.8 MB)
[*] Online documentation: [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")
[/LIST]

---

### Post by Grenage on 2010-04-28
Follow **Leppie**'s instructions:

```
sudo apt-get install testdisk
sudo photorec
```

---

### Post by BadlyNeedHelp on 2010-04-28
I done what you said,

ubuntu@ubuntu:~$ sudo apt-get install testdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package testdisk
ubuntu@ubuntu:~$ sudo photorec
sudo: photorec: command not found
ubuntu@ubuntu:~$

---

### Post by Grenage on 2010-04-28
Ok:

System/Administration/Software Sources

In the 'General' tab, make sure that everything except 'source code' is ticked.  If it asks you to reload, do so - then try and install testdisk again.

---

### Post by BadlyNeedHelp on 2010-04-28
Yeah everything except source code was clicked, this is really frustrating to be honest, I really need my pictures and videos back :'(

---

### Post by mike555 on 2010-04-28
You do know you can't install programs to Ubuntu when running the live from CD, right ......

---

### Post by wojox on 2010-04-28
Did you mount the drive before you downloaded these files?
What OS is currently installed on the HDD?

---

### Post by BadlyNeedHelp on 2010-04-28
Well you can, because I have installed Adobe Flash Player running Ubuntu on the Disk without installing..

---

### Post by Grenage on 2010-04-28
> **mike555 said:**
> You do know you can't install programs to Ubuntu when running the live from CD, right ......

What? Sure you can.

---

### Post by BadlyNeedHelp on 2010-04-28
> **wojox said:**
> Did you mount the drive before you downloaded these files?
What OS is currently installed on the HDD?

What do you mean "Mount The Drive"? Currently I have Windows Vista installed, but I cannot get it to work, system repair keeps saying "Windows cannot automatically repair this system" so I'm using Ubuntu, running it from the Disk.

---

### Post by wojox on 2010-04-28
Did you click on the hard drive or download anything to /media/one_big_number?

---

### Post by mike555 on 2010-04-28
silly me , I thought CD-r's were read only after being burned .........


perhaps you are just using the live disc to install something on an installed operating system?

---

### Post by BadlyNeedHelp on 2010-04-28
> **wojox said:**
> Did you click on the hard drive or download anything to /media/one_big_number?

I didn't do that no, I don't even know how to use Ubuntu its so confusing.

All I need to do is find a recovery software that will recover my memory card from my Camera so I can get my Pictures and Videos back.

I just can't seem to find any software that's free, that works within Ubuntu.

---

### Post by wojox on 2010-04-28
Well take your memory card and put it back in your camera so it's safe. Then install Ubuntu on the drive. Then you can install testdisk from the repo's and fix your card.

---

### Post by mike555 on 2010-04-28
I would recommend getting PartedMagic live cd , it has photo restore programs on it ...
 [http://www.techmixer.com/free-hard-disk-rescue-cd-parted-magic/](http://www.techmixer.com/free-hard-disk-rescue-cd-parted-magic/)

---

### Post by Grenage on 2010-04-28
> **mike555 said:**
> silly me , I thought CD-r's were read only after being burned .........


perhaps you are just using the live disc to install something on an installed operating system?

It stores the app in memory, I install and run apps using the LiveCD all the time.  What are you talking about?

---

### Post by mike555 on 2010-04-28
sure you can "install" apps temporarily , but when you restart the "installed " things are gone ................ I wanted to let the poster know that so he/she would not wonder where the pictures went ....... 

of course he/she could use Ubuntu to get photos then write them to a thumbdrive for safe keeping ...

---

### Post by varunendra on 2010-04-28
Hey buddy,

Just pm (personal Message) me your email and I'll mail you the .deb package of testdisk. It is only 1.5MB in size.

After you get the.deb package (from me or somewhere else), all you need to do is to double-click the package to install it, just as you do in Windows. The remaining steps are next-next-finish type (again as in windows:))

Alternatively, you can try downloading "System Rescue Disk" which is a CD image (.iso format) that you can busn on a cd using Nero or any cd -burning app.

It is a live cd & contains everything preinstalled- ready to use. Everything you may need !
But of-course much larger in size than the standalone testdisk package I can mail you !:popcorn:

PS. I'll be back in half an hour.

---

### Post by Grenage on 2010-04-28
> **mike555 said:**
> sure you can "install" apps temporarily , but when you restart the "installed " things are gone ................ I wanted to let the poster know that so he/she would not wonder where the pictures went ....... 

of course he/she could use Ubuntu to get photos then write them to a thumbdrive for safe keeping ...

Understood; figured we had wires crossed somewhere!

---

### Post by BadlyNeedHelp on 2010-04-28
> **varunendra said:**
> Hey buddy,

Just pm (personal Message) me your email and I'll mail you the .deb package of testdisk. It is only 1.5MB in size.

After you get the.deb package (from me or somewhere else), all you need to do is to double-click the package to install it, just as you do in Windows. The remaining steps are next-next-finish type (again as in windows:))

Alternatively, you can try downloading "System Rescue Disk" which is a CD image (.iso format) that you can busn on a cd using Nero or any cd -burning app.

It is a live cd & contains everything preinstalled- ready to use. Everything you may need !
But of-course much larger in size than the standalone testdisk package I can mail you !:popcorn:

PS. I'll be back in half an hour.

Thanks, I will do that.

In other news, I have installed Ubuntu, I'm not happy about doing it but I't had to be done. Knowing my luck now, I won't be able to recover my pictures and videos.

---

### Post by wojox on 2010-04-28
You should be able to downloaded it now per leppie and grenage's instructions. You needed an OS anyway.

---

### Post by Grenage on 2010-04-28
Since you've installed Ubuntu, try installing teskdisk again (sudo apt-get install testdisk).

You've as much chance of recovering your pictures now as you did before, you're recovering stuff from the memory card in the camera, not the computer.

---

### Post by Leppie on 2010-04-28
> **mike555 said:**
> You do know you can't install programs to Ubuntu when running the live from CD, right ......
that is not correct, you can install applications provided you do have enough ram for that. furthermore applications installed in the live environment are discarded at reboot if no partition is assigned to make modifications persistent.

---

### Post by BadlyNeedHelp on 2010-04-28
I will try again,

But what one do I need to download?


[LIST]
[*] [IMG]http://www.cgsecurity.org/os/dos.png[/IMG] [Dos/Win9x]("http://www.cgsecurity.org/testdisk-6.11.3.dos.zip")
[*] [IMG]http://www.cgsecurity.org/os/win.png[/IMG] [Windows]("http://www.cgsecurity.org/testdisk-6.11.3.win.zip")
[*] [IMG]http://www.cgsecurity.org/os/linux.png[/IMG] [Linux]("http://www.cgsecurity.org/testdisk-6.11.3.linux26.tar.bz2"), kernel  2.6.x i386/x86_64
[*] [IMG]http://www.cgsecurity.org/os/linux.png[/IMG] [Linux]("http://www.cgsecurity.org/testdisk-6.11.3.linux24.tar.bz2"), kernel  2.4.x i386/x86_64
[*] [IMG]http://www.cgsecurity.org/os/rpm.png[/IMG] Linux [i386 RPM]("http://www.cgsecurity.org/testdisk-6.11.3-1.i386.rpm")
[*] [IMG]http://www.cgsecurity.org/os/rpm.png[/IMG] Linux [SRPM]("http://www.cgsecurity.org/testdisk-6.11.3-1.src.rpm")
[*] [IMG]http://www.cgsecurity.org/os/mac.png[/IMG] [Mac OS X]("http://www.cgsecurity.org/testdisk-6.11.3.darwin.tar.bz2")
[*] [IMG]http://www.cgsecurity.org/os/os2.png[/IMG] Non official version of [PhotoRec for OS2]("http://www.fbakan.de/photorec-os2.htm")
[*] [Source code]("http://www.cgsecurity.org/testdisk-6.11.tar.bz2") - [Patch v2 for PhotoRec]("http://www.cgsecurity.org/photorec_611_exif_bound_checking_v2.patch") adding missing boundary check in EXIF processing
[*] Documentation to download: [bz2 archive]("http://www.cgsecurity.org/testdisk-doc-6.11.tar.bz2") (2.9 MB), [zip archive]("http://www.cgsecurity.org/testdisk-doc-6.11.zip") (3.8 MB)
[*] Online documentation: [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk"), [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec")
[/LIST]

---

### Post by Grenage on 2010-04-28
Try using APT-GET first as mentioned earlier in this thread.

---

### Post by Leppie on 2010-04-28
what is the output of the following command?
```
sudo apt-get update
```

you will have to enable the "Universe" repository:
- go to System > Administration > Software Resources
- make sure the option "Community maintained Open Source software (universe)" is checked.

---

### Post by BadlyNeedHelp on 2010-04-28
admins@admins-laptop:~$ sudo apt-get install testdisk
[sudo] password for admins: 
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
admins@admins-laptop:~$ 




Sooooo confusing!!!!! :confused:

---

### Post by CharlesA on 2010-04-28
Do you have update manager or software center running?

---

### Post by posburn on 2010-04-28
It looks like you have Synaptic Package Manager open at the same time as you are trying to enter the terminal commands. Do one or the other but not both at the same time. I would close Synaptic and retry the terminal commands.

---

### Post by varunendra on 2010-04-28
Just mailed you the .deb package. Did u get it?

---

### Post by BadlyNeedHelp on 2010-04-28
YAY :D :D :D 

It worked, and I got all my pictures and videos back! :D

I cannot thank you enough guys, thank you so so so much! :P:P:P

---

### Post by BadlyNeedHelp on 2010-04-28
> **varunendra said:**
> Just mailed you the .deb package. Did u get it?

Thanks for sending that, haven't checked yet but I don't need it anyway now, it worked without using the thing you tried to send! thanks anyway! :)

---

### Post by CharlesA on 2010-04-28
Don't forget to mark the thread as solved: Thread tools > Mark as solved.

---

### Post by varunendra on 2010-04-28
> **BadlyNeedHelp said:**
> YAY :D :D :D 

It worked, and I got all my pictures and videos back! :D

I cannot thank you enough guys, thank you so so so much! :P:P:P

Hey YAY to whome? My package can't be that fast !

And remember: There's no other forum out there u can find as helping as this one. PLUS- Ubuntu's best. Accidents can happen anywhere, especially when u don't know the rules.

Cheers!!:popcorn:

---

### Post by BadlyNeedHelp on 2010-04-28
> **CharlesA said:**
> Don't forget to mark the thread as solved: Thread tools > Mark as solved.

Done :P I'm so happy now, thanks so much guys!

---

### Post by BadlyNeedHelp on 2010-04-28
Ok so after successfully recovering my pictures/videos, some of the videos play half way and then say "Failed to decode JPEG Image" anyone know how to solve this?

I have also tried recovering my SD Card again, but the testdisk just wont work, it wont let me recover anything.

I don't understand this bit:

Use arrow keys to select, then press Enter key:
[ Create ]  Create a new log file
[ Append ]  Append information to log file
[ No Log ]  Don't record anything


I clicked on "No Log", and this came up,

Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
[Sun    ]  Sun Solaris partition
[XBox   ]  XBox partition
[Return ]  Return to disk selection



First time i recovered my SD card successfully, I used "None", when I try and recover it again, I do exactly the same as I did the first time and it just don't work.

So after clicking "None, this comes up, again I'm confused:

[ Analyse  ]  Analyse current partition structure and search for lost partitions
[ Advanced ]  Filesystem Utils
[ Geometry ]  Change disk geometry
[ Options  ]  Modify options
[ Quit     ]  Return to disk selection



Theres no option for me to recover.

---

### Post by Leppie on 2010-04-28
most camera's use a fat filesystem for the memory cards from the Intel/PC partition family.

---

### Post by varunendra on 2010-04-29
> **BadlyNeedHelp said:**
> 
Please select the partition table type, press Enter when done.
[Intel  ]  Intel/PC partition
[EFI GPT]  EFI GPT partition map (Mac i386, some x86_64...)
[Mac    ]  Apple partition map
[None   ]  Non partitioned media
Follow what Leppie said. AFAIK, no company uses any format other than  FAT/FAT32 for its removable storage units. That is Intel/PC partition.


> **BadlyNeedHelp said:**
> some of the videos play half way and then  say "Failed  to decode JPEG Image"
 Was your card full? Did you frequently (partly) deleted & added  videos/pics on that card? If that's the case, then most probably your  card was fragmented, i.e., files were scattered in pieces.
Although this is no reason to worry if the partition table of the card  is intact and no overwriting has been done on it.

But you said that Ubuntu was crashed when you lost your files. If the  card was plugged in and was in use at that time, then there is a slight  possibility that your card's partition table might also have been  damaged.
In this case, testdisk or any other undelete/recovery software - no  matter it is linux or windows based - would only recover the starting  portion of the "fragmented" files. As a result, such "incomplete" files  can only be read to the extent they were intact from the starting point.
The most a recovery program can do in this case is to recover the  scattered, lost "parts" as well but in form of separate, unknown files  having no idea of their format or which files they are parts of.

So first retry testdisk to see if your files are listed, (either "none"  or "Intel/PC" should work, try testdisk's default selection first) then  recover them using "undelete" option and recheck if they are complete.
To me there seems no reason why testdisk can't list them. It must,  regardless of whether the files were fragmented or not.

If among the set of files recovered this time, the same files that  failed to play completely earlier fail this time also, then definitely  these files were fragmented, PLUS card's partition table is partially or  completely damaged.

Well... I don't want to scare you, especially after seeing so many  smileys on your earlier post, but there's little hope to get them intact  again.:(

You can try some advanced tools like GetDataBack for FAT/FAT32 (windows  based, should work over wine) or R-Tools. Let me add that "R-Tools" and  "R-tools emergency" have done miracles to me in the past. But these  software are commercial & trial versions would only let you see the  files, won't recover them.
Goodluck[-o<

---

