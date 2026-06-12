---
title: "Install Breezy - sys doesn't support boot from CD"
date: 2006-03-15
forum: General Help
---

### Post by Optiker on 2006-03-15
Trying to install Breezy Badger on an older system. It doesn't support boot form CD. The documentation talks about booting from system HD with install files on HD, but doesn't go into any detail - which install files, where are they on CD, where do they go on HD, how do you launch them once the sys is booted?

Can anybody help? Details?

Thanks!

Optiker

---

### Post by rattking on 2006-03-16
I have an idea.. on the Freedos boot disk there is an option for Smart Boot Manager.. this supports booting from cd and many others
download the floppy image here
[http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/old/beta9sr2/fdos1440.img](http://www.ibiblio.org/pub/micro/pc-stuff/freedos/files/distributions/old/beta9sr2/fdos1440.img)
you can write the image to a floppy with the command
dd if=fdos1440.img of=/dev/fd0
boot that floppy and choose option 2 Smart Boot manager
select CD-ROM from the boot menu
and hopefully your system will boot from cd
good luck

---

### Post by Optiker on 2006-03-16
Rat...

Cool! Thanks! Will try it and get back with results...probably this evening or over the weekend.

Optiker

---

### Post by Optiker on 2006-03-16
Rat...

How do I do this? Is this a command line instruction for a Windows Command Prompt? Typing it in the command prompt doesn't seem to work.
--------------
you can write the image to a floppy with the command
dd if=fdos1440.img of=/dev/fd0
--------------


Thanks!
Optiker

---

### Post by rattking on 2006-03-16
thats a linux command..
in windows you need a program called rawrite it should be on that server 
or you can google it..

---

### Post by Optiker on 2006-03-17
Rat...

OK - got it. Had a feeling that might have been the case, and since I don't have Linux on the system, didn't help.

I found the extensive compilation of rawrite utilities at [http://www.fdos.org/ripcord/rawrite/](http://www.fdos.org/ripcord/rawrite/) and DLed several each - some even with documentation - for DOS and Windows, so I'm sure I can make something work.

Will probably try it all this evening, so will report back then, or tomorrow.

Thanks for sticking with me.

Optiker

---

### Post by Optiker on 2006-03-20
Rat...

Sorry didn't get back sooner - got distracted.

Based on the recommendations on the fdos site, used RawWriteWin to write the img to floppy, ran the utility, and shazam! Worked great! Kubuntu installed and other than the typical problems with sound and getting all of the right partitions seen and mounted, looking good! It runs a bit slow as one might expect from a 200 MHz cpu! But, still, will do fine for the intended purposes.

Thanks!
Optiker

---

### Post by lordofkhemenu on 2006-03-20
[quote=Optiker]Rat...

Sorry didn't get back sooner - got distracted.

Based on the recommendations on the fdos site, used RawWriteWin to write the img to floppy, ran the utility, and shazam! Worked great! Kubuntu installed and other than the typical problems with sound and getting all of the right partitions seen and mounted, looking good! It runs a bit slow as one might expect from a 200 MHz cpu! But, still, will do fine for the intended purposes.

Thanks!
Optiker[/quote]
Glad you got breezy going.
KDE is kind of a cpu intenstive DE to use on that lil ol machine.
 Try [IceWM]("http://icewm.org/") or [WindowMaker]("http://windowmaker.org") - it'll be less of a strain on that lil ol CPU. Not quite as much eye candy, but you can still make them look pretty. ;)

---

### Post by lnunes on 2006-03-30
Hey!

Well, I have a very funny situation :twisted:  here....

I have an OLD lap here, that has an USB cd-rom... :mrgreen: 

well, SBM doesn't work to me, cause he attempts to find a IDE cdrom... I have another linux dist installed (slackware), and the other tips (download kernel, create a c:\boot, etc...) doesn't work too....

Anyone can help me with this?? :confused:

---

### Post by usergentoo on 2006-03-30
can you do a network boot and use another computer to install it. See if the cmos has that option.

I seen a floppy disk for another distro the other day and it allows you to choose what to boot from usb flash drive,usb cdrom, cdrom, network, hardrive. Ive got it but i cant figure out who made it I somehow corrupted the floppy. It starts off booting into freedos then it asks where you want to boot from. Im thinking I saw this on a site on how to install puppy linux but not sure already checked a few sites for it but no luck. If I find it Ill post back with the info.

---

### Post by rattking on 2006-03-30
here is the link to that puppy linux loader 
[http://www.murga.org/~puppy/viewtopic.php?t=3875](http://www.murga.org/~puppy/viewtopic.php?t=3875)
give it a try and report back.. i am not really sure if this can load anything or just puppy linux..

---

### Post by usergentoo on 2006-03-30
[http://btmgr.webframe.org/](http://btmgr.webframe.org/)
its called smart boot
this is the other one I was looking for and it works well but not sure if you can boot usb cdroms but maybe its worth a try. This little prog should be added to the how to section.I couldnt tell you how many times Ive used this.

---

### Post by lnunes on 2006-03-31
[QUOTE=rattking]here is the link to that puppy linux loader 
[http://www.murga.org/~puppy/viewtopic.php?t=3875](http://www.murga.org/~puppy/viewtopic.php?t=3875)
give it a try and report back.. i am not really sure if this can load anything or just puppy linux..[/QUOTE]


Ok, it really works, now I have my USB booting. I can boot a Pen Drive, but cannot boot a bootable cd-rom. As I can saw, the usb device needs to have a PUPXUSB blank file. I tried to burn a new Ubuntu install CD with this blank file, without success. ](*,) 

I missed something? :confused:  How can I boot the ubuntu install CD ?

---

### Post by usergentoo on 2006-03-31
inside that floppy file you can find autoexec.bat
make that file look for the boot file in ubuntu i think its vmlinuz. Here is what the file looks like maybe someone could add to something I said.

```
MSCDEX.EXE /D:MSCD001 /L:G

rem

rem (c)2004 Barry Kauler, www.goosee.com/puppy

rem I can't remember much how to write DOS batch files!

rem

echo off





:STEP2

rem This block is any usb msdos/fat/vfat memory, needs file pupusb...

if NOT EXIST C:\pupxusb goto STEP3

echo on

rem Loading Puppy from the USB drive...

tiny.exe C:\vmlinuz C:\image.gz root=/dev/ram0 PROOTFS=umsdos PSLEEP=25

goto end

:STEP3

if NOT EXIST D:\pupxusb goto STEP4

echo on

rem Loading Puppy from the USB drive...

tiny.exe D:\vmlinuz D:\image.gz root=/dev/ram0 PROOTFS=umsdos PSLEEP=25

goto end

:STEP4

if NOT EXIST E:\pupxusb goto STEP5

echo on

rem Loading Puppy from the USB drive...

tiny.exe E:\vmlinuz E:\image.gz root=/dev/ram0 PROOTFS=umsdos PSLEEP=25

goto end

:STEP5

if NOT EXIST F:\pupxusb goto STEP6

echo on

rem Loading Puppy from the USB drive...

tiny.exe F:\vmlinuz F:\image.gz root=/dev/ram0 PROOTFS=umsdos PSLEEP=25

goto end



:STEP6

rem This block for IDE drives, needs file pupxide to identify...

if NOT EXIST C:\pupxide goto STEP7

echo on

rem Loading vmlinuz and image.gz from the C: drive...

tiny.exe c:\vmlinuz c:\image.gz root=/dev/ram0 PFILE=pup080-none-262144

goto end

:STEP7

if NOT EXIST D:\pupxide goto STEP8

echo on

rem Loading vmlinuz and image.gz from the D: drive...

tiny.exe D:\vmlinuz D:\image.gz root=/dev/ram0 PFILE=pup080-none-262144

goto end

:STEP8

if NOT EXIST E:\pupxide goto STEP9

echo on

rem Loading vmlinuz and image.gz from the E: drive...

tiny.exe E:\vmlinuz E:\image.gz root=/dev/ram0 PFILE=pup080-none-262144

goto end



:STEP9

rem This block handles booting off cdrom...

echo on

rem Failed to find Puppy on C:, D:, E:, F: drives, now trying cdrom...

rem (which is the G: drive)

rem Hit "F" (Fail) key if this step fails...

if NOT EXIST G:\image.gz goto STEPF

rem Loading Puppy from CDROM...

tiny.exe G:\vmlinuz G:\image.gz root=/dev/ram0 PFILE=pup080-none-262144

goto end



:STEPF

echo on

rem Failed to find Puppy on C:, D:, E:, F: or G: drives.

rem (I'm assuming that vmlinuz and image.gz are somewhere!)

rem (note, place empty file "pupxusb" on usb drive as AUTOEXEC.BAT

rem  uses it to identify that drive is a USB msdos/fat/vfat drive)

rem (note, place empty file "pupxide" on IDE drive as AUTOEXEC.BAT

rem  uses it to identify that drive is a IDE msdos/fat/vfat drive)

rem (...but only create pupxusb or pupxide on drive which has Puppy)

rem (...the cdrom does not need any special identifier file)

:end
```

---

### Post by lnunes on 2006-03-31
sorry, this code (pasted on autoexec.bat) doesn't work...

---

### Post by lnunes on 2006-04-03
ok, I made!

steps:

I'd copied all files to a USB disk, and included the PUPXUSB file in the root of usbdisk; booted with the puppy disk, and manually run the command ()note that my 'C:' is my USB disk):

c:\install:>a:\lindl image=vmlinuz initrd=initrd "cl=root=/dev/ram0"

In the middle of installation, when it looks for a disc to read files from, I've disconnected tue USB disk and connected my USB cd-rom.

Now I'm having fun installing ubuntu....

---

### Post by Al3xanR0 on 2006-04-04
[QUOTE=lnunes]

Now I'm having fun installing ubuntu....[/QUOTE]

\\:D/  That's awesome rock on!

---

