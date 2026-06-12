---
title: "Crashed System Status 3, Mount of filesystem Failed, left at root @ maintenance shell"
date: 2010-10-03
forum: General Help
---

### Post by Ronok on 2010-10-03
[SIZE="1"]Crashed System left at root @ maintenance shell[/SIZE]

Below is the _sequence_ after _boot_, with _Exact Errors_

**Please Help** me to _Salvage_ important files from my crashed laptop hardware

**A)** Via a _Transfer_ to a _USB_ stick in Terminal, would be ok
**B)** _Via SSH_ through the router from the good laptop that is Preferably using Nautilus / GUI,  Terminal also ok (less confident of my skill here)
**C)** _Directly Fixing Laptop_ and being ably to use Nautilus / GUI to Copy Files to USB stick, localy

The result of some effort:
[B]
A)[/B] the USB stick is good but Can't get in to it from the crashed laptop 
**B)** SSH: No luck I get: "Cannot display location "sftp://192.168.1.101/"" from the good Machine
**C)** at a lose here...

_The Crashed Laptop is:_

Ubuntu: 9.10
Linux: 2.6.31-22-generic
Gnome: 2.28.1
CPU: Intel Atom N280 @ 2GHz
NO: CD / DVD Drive 
[SIZE="1"](USB Boot maybe possible ? Have not made a Bootable Ubuntu USB Yet)[/SIZE]

**BOOT:**

GNU GRUB Version 1.97~
Ubuntu, Linux 2.6.31-22-generic
etc / (& recovery mode)

mini Ubuntu logo or splash screen

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171174&d=1286101118[/IMG]

File-system checks are in progress _sticks every time_ at 4%

**init: mountall main process (418) terminated with status 3**
#(it seem to count up every time I re try to boot ? (init: mountall main process (423)(429)(etc)
[B]Mount of filesystem Failed.
A maintenance shell will now be started.[/B]
CONTROL-D will terminate this shell and re-try
**root**@Bi-Ji-Ben**:~#**

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171175&d=1286101118[/IMG]


I can navigate around but cant get the GUI up
root@Bi-Ji-Ben:~# nautilus
could not Parse arguments: Cannot open display:

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171176&d=1286101118[/IMG]

a good USB stick reads & writes in another laptop running Ubuntu 9.10 

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=171177&d=1286101118[/IMG]

when I connect the USB to the Crashed Machine it starts with:
"assuming drive cashe: write through", 
and hangs on this tell I press: "Ctrl+C"

in the crashed machine I can't seem to get in to the USB anywhere that I think it should show up
and trying to "mkdri" got me: "Read only file system" 

[IMG]http://art.ubuntuforums.org/attachment.php?attachmentid=171138&d=1286078930[/IMG]

**Thanks Very much for any Help**
See a Little of my post about Linux & Ubuntu Here:
[URL="http://www.gongkuo.com/linuxcli.htm"]My < Linux > Command Line Interface Page
http://www.gongkuo.com/linuxcli.htm[/URL]

---

### Post by P4man on 2010-10-03
You really want to boot from an ubuntu USB stick to salvage your files. Its the first thing to try really. If the hdd is badly messed up and you cant mount the drive to copy files from it, have a look at testdisk and photorec.

---

### Post by Ronok on 2010-10-06
**Thank You: _P4man_**

Thanks for your suggestion about Boot from a Ubuntu USB
**See Details Below for How I Successfully Got My Files Out of the My Crashed Laptop**
(for anyone following after this with similar issues)

... a little background, the Hardware had issues from the start [(_see_)]("http://ww.ubuntuforums.org/showthread.php?t=1379064")
This Particular Laptop was a:"Cheap-NO-Brand-New-parking-lot-purchase"
Bright side: Had previously backed up 90% of my files and
UBUNTU is a grate Operating System so I am continuing with it 
now on a different & Branded Laptop [_(see SamSung N148)_]("http://www.ge.ubuntuforums.org/showthread.php?t=1583449")

**Steps I used to Salvage Files From Crashed Laptop:**

**1)** download an Ubuntu-image.iso

> [http://releases.ubuntu.com/](http://releases.ubuntu.com/)

**2)** I used gparted to wipe clean a USB stick that I had

> System > Administration > Gparted 

**3)** I used: "USB Startup Disk Creator" to write the .iso image 
onto the USB stick (I have tried it successfully with each: Ubuntu, Xubuntu, & Crunchbang)

> System > Administration > USB Startup Disk Creator

**4)** put it in before the boot on the Crashed machine,

**5)** Maybe need to press: "F2" or "Del" to get into the Bios 
and change the boot priority to Boot from USB + #1 in more than one place

**6)** Choose language, 
Choose: "Try Ubuntu without any change to your computer" 

**7)** in this environment Ubuntu wont make any "changes to your computer"
so to get past that I had to open a "Terminal" and become a "Super User" 
(a privileged user that can make Changes to a Computer even in the "Live CD or USB" environment, 
**Caution !** privilege = Power to make a mistake also)
First open a Terminal:

> Applications > Accessories > Terminal

**8)** then Become "Super User" 
there may be a number of ways to use elevated privilege 
but I did not want to type **sudo** in front of everything 
Caution! the following command seems to make me: " root@laptop:~# "
"**root**" = same **Caution** as **#7** above But it does first ask
[sudo] password for [user]: _____.

```
sudo /bin/bash
```

**9)** need to see: "fdisk" Partition table manipulator to see where disks are mounted, if their mounted & additional info 


```
fidsk -l
```

**10)** I made a place for the Device or Disk to be mounted at
**Note** the Name: "crash888" is just the name I chose, if someone else, the name can be different for each situation

```
mkdir /media/crash888
```

**11)** then I need to get that portion of disk mounted
(the one that has the files I want still on it)
Note: "/dev/sda1/" might be diffrent in someone else case
Note: "mount /dev/sda1/[one space here]/media/crash888

```
mount /dev/sda1/ /media/crash888
```

**12)** I wanted to get a "File-Browser" open to move files around with the Mouse & GUI
I did a lot of the work undder XUbuntu so I actually used: gksudo thunar /media/crash888

```
gksudo nautilus /media/crash888
```

**13)** I wanted another nautilus File-Browser open to the destination for the files, 
a Second Bigger USB disk, it automatically showed up in: "/media/"
get its [some name here*] by listing the media:

```
ls /media/
```

then open it:

```
gksudo nautilus /media/[some name here*]
```

**14)** the File-Browser Crashing, it did give me a rather long error message
in the terminal, 
I will post it here later on an Edit, 
so my solution was to just copy the files I wanted working from within the Terminal
Copying:
from (your own source path, disk, folder or name: [/a/a/a] )
to (your own destination path, disk, folder or name: [/b/b/b] )
"-R" for copy all the sub-folders also

```
cp -R /media/a/a/a/ /media/b/b/b/
```

**15)** when I got all the files transfered into the new laptop I had some problem with ownership, 
this is how I fixed that for all the files Note: "yournamehere" = your user name without **"**quotes**"**

```
chown "yournamehere" -R /media/222
```

**16)** for some of the files I needed to be a "Super User" First
see **#7** above, then do the above code

---> well I got all my files Back  :-)

**NEXT:** 
I am now having trouble with "**gparted**" 
cleaning or clearing the Hard Disk for a **new install**, 
some **errors !** I will post them clearly here on a later edit
aprox: (/dev/sda1/ will not format when unmounted, or stay visable in "fdisk -l)
I am looking over the Manual pages as follows for now:

```
man fsck
man shred
```

**Thank You Very Kindly** for any Additional 
Help, inspiration or insight

See a Little of my post about Linux & Ubuntu Here:
[URL="http://www.gongkuo.com/linuxcli.htm"]My < Linux > Command Line Interface Page
http://www.gongkuo.com/linuxcli.htm[/URL]
Ronok

---

