---
title: "Help Installing D#&amp;! Small Linux on Hard Drive old Gateway"
date: 2011-01-28
forum: General Help
---

### Post by 4042966262 on 2011-01-28
Trying to install D%#! Small Linux as the Main (and only!!) os on an old gateway computer. Had a issue getting Cd to boot but was told to swap drive from another PC Loads perfect now!! I can use the pc from disk..but I want it installed to hard drive!1 how do I do this?

sudo -u root dsl-hdinstall

after this code is entered I get 
do you wish to support multi user logins (I typed y)
use journalized ext3 fileysyrem (not recommended for slower machines) (I typed n)
last chance to exit!! (i typed y)
creating filesystem ext2 on /dev//dev/hda1
an error occurerd whiel creating this filesystem.
Some messages deom mkfs.
Mk2.fs 1.34-WIP (21-May-2003)
could not start /dev//dev/hda1
the device apparently dose not exist did you specify it correctly?

Apparently not. What am I doing wrong?
[http://www.uluga.ubuntuforums.org/showthread.php?p=6371783](http://www.uluga.ubuntuforums.org/showthread.php?p=6371783) (this is the Tut I was using)
I never made a partition. Don't know how

---

### Post by gbrainin on 2011-01-28
I've never used DSL, much less installed it to anything, but I found this that might be helpful: [http://www.damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk]("http://www.damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk")

---

### Post by 4042966262 on 2011-01-28
ehh..not so helpful. i was there, any more advice?

---

### Post by tgalati4 on 2011-01-28
Boot into the BIOS and make sure the drive shows up.  Sometimes swapping drives from machines and changing cables requires you to reconfigure the BIOS to detect the new drive.  Also check the jumper on the back of the drive.  Select Master is you plan on using this as your primary boot drive.  Set any other drive as Slave on the same ribbon cable.

---

### Post by gbrainin on 2011-01-29
Since you can get DSL to load from CD, can you post the output from:```
sudo fdisk -l
```

---

### Post by ugm6hr on 2011-01-29
> **gbrainin said:**
> I've never used DSL, much less installed it to anything, but I found this that might be helpful: [http://www.damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk]("http://www.damnsmalllinux.org/wiki/index.php/Installing_to_the_Hard_Disk")

> **4042966262 said:**
> I never made a partition. Don't know how

This is the problem. gbrainin's link above is your solution, albeit with minor modification.

```
sudo -s
cfdisk /dev/hda
```

It is possible that your HD is not hda (although unlikely, if it is genuinely an old HD) - hence the command above won't be able to create a partition on a non-existent HD!

Try:
```
sudo -s
cfdisk
```
This generally finds the main HD. 

PS: fdisk -l will list all drives, allowing you to modify the cfdisk command specifically.

---

### Post by 4042966262 on 2011-01-29
ok poeple's here's what i have.

**i typed**   f disk -1
invalid option--1
busybox v1.2.2 (2006.120.07-15:23+0000)
multi-call binary
usage: fdisk [-luv] [-c cylinders] [-h heads] [-s sectors] [-b ssz] DISK
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~<-- shows end of code
Next Code
sudo -s
cfdisk
Fatal Error can not open Disk Drive Press Any Key To Exit cfdisk
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~<shows end of code
and the stuff about running in BIOS and checking drive>? and something about a slave? WAAAAY over my head. could you reexplain that?:confused:

~~~~PS thank you guys so much for trying to help me with this stuff. i hope it makes more sence to you thean it dose me!!:redface:

---

### Post by gbrainin on 2011-01-29
You need to be careful when copying commands.  The command is "fdisk" not "f disk" and, more importantly, the switch is "-l" (the lower-case letter "L") not "-1" (the number one).  "fdisk" is the basic *F*ixed *DISK* (*i.e.*, hard drive) manipulation program for Linux, and the -l switch tells it to just *L*ist what it finds, and not make any changes.

Also, since you are manipulating hardware, it is critical that you use the sudo command beforehand.  That escalates you to "super user" status for that one command.  Without it, the "fdisk -l" command will have no output.

That having been said, the error that you got when using the cfdisk command seems to indicate that there's some sort of hardware problem.  I'm _guessing_ that you'd get a similar error from "sudo fdisk -l" (though trying it won't hurt).  Unfortunately, the several things that tgalati4 mentioned above (BIOS settings, ribbon cable, master/slave configuration) can all lead to the same symptom (hard drive not "seen" by the operating system).  So you just have to try all of them.

BIOS: The way these screens look differs widely from one computer to the next, so I can't really walk you through it.  However, I see that you were able to get some hardware settings, which means you can get into the BIOS setup screen.  Somewhere in one of the menus/screens ought to be something that shows the status/configuration of the hard drives.  You need to make sure that a) the BIOS can see that there is a hard drive, and b) that the settings are correct.  If you're lucky, the BIOS will have an autodetect function.  If not, you'll have to get the settings for your drive, either from the drive label or the manufacturer's website.

Cable: Assuming you have an IDE hard drive (a reasonable assumption, given the age of the computer), there should be two cables plugged into the back of the drive: A power cable (four colored wires and a clear/white plastic connector; other end goes to the power supply) and a data cable (wide thin ribbon cable, usually grey; other end goes to the motherboard, or possibly to a daughter board if your computer is old enough).  If either of these cables is not making a good connection, that could cause your problem.  Even if it looks like they're connected, unplugging and replugging them ("reseating") can sometimes help.  Be careful with the data cable, as it is possible to bend pins if you don't push it on squarely, and many older systems do not force the cable on the right way (*i.e.*, you could connect it upside-down, which would not work).

Master/slave: Long story why this even exists.  Somewhere on the hard drive there are likely a bunch of pins that may or may not have a jumper on them.  Where the jumper is placed determines the drive's master/slave status.  If you're lucky, there is a diagram of this on the hard drive label.  If not, try googling the hard drive's manufacturer and model number.  Failing that, google "hard drive master slave setting" or similar.

---

### Post by 4042966262 on 2011-01-29
how did i forget the ever so important sudo??
just typed in terminal sudo fdisk -l and it gives little blinky # sign. waiting for more commands i guess? as for BIOS and Slave. ill look for that

---

### Post by gbrainin on 2011-01-29
After you enter the command "sudo" and whatever, it usually asks for your password.

Edit: If you're booting from a CD, you probably don't have a password (*i.e.*, just hit enter).

---

### Post by 4042966262 on 2011-01-31
tried the code that was suggested, got the FATAL ERROR message. and i don't think terminal was waiting for a password. the # lets me type, and if i hit enter, (no pass set booted from CD) i get a command not found error. thus i _think_ its asking for a code. hmm.. this is quite a paradox.

---

### Post by gbrainin on 2011-01-31
I'm a little confused.  I thought you were typing the command and getting no output, just a new line with # at the beginning.  If you're getting output (the fatal error message) _then_ the new line with #, then it seems that # is your command prompt.  That is, it's your system saying "I'm done with what you asked me to do; what's next?"

Which brings me back to the idea of a hardware problem.  It sounds like your system can't see the hard drive, or is getting some unrecoverable error message from it.  Have you tried getting into the BIOS screen and seeing if it recognizes your hard drive?

---

### Post by 4042966262 on 2011-02-01
i tried all the commands. the one that gave me fatal error ''cfdisk'' would only allow me to press any key to exit then change back to terminal. this is  not. what i was talking about. thats another code located someonewhere on here.. i can't quite remember it. yes i can boot into BIOS. how do i see if ir ''recognizes my hard drive''?

---

### Post by ugm6hr on 2011-02-02
Evert computer has a different BIOS setup - so just look through the menus.
It should have a list of internal HDs somewhere.
Clearly, the OS cannot find any evidence of a HD at all - hence the failure of cfdisk / fdisk to locate them. This may be a hardware problem, or, as previously suggested, may relate to a jumper switch setting on the hard drive itself being incorrect.
A search of the HD manufacturer site should find an instruction sheet on how to change it.

---

### Post by 4042966262 on 2011-02-05
thank you for all your help guys!! i figured it out though, install Lubuntu.  ~thread solved

---

