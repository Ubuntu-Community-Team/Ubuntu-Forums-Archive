---
title: "Dual booting Ubuntu with Windows 7"
date: 2011-01-23
forum: General Help
---

### Post by Ron W on 2011-01-23
I've just got a Toshiba NB 250 netbook pre-loaded with Windows 7.

I'm hoping to dual boot this (Windows 7) with Ubuntu. There are three partitions (sda1, sda2, and sda3) already created on the disk. I'm thinking of reformatting the sda3 drive to EXT4 and loading Ubuntu onto this drive. I'm not sure what's on sda1, but sda2 appears to have the windows 7 on it (though I'm not sure about that).

I would be very grateful for any advice, suggestions, pitfalls with the method, etc.

Thanks

Ron

---

### Post by MooPi on 2011-01-23
Be careful as one of those partitions is most likely a reinstall for Windows 7 or recovery partition. Can you give us the sizes of each partintion. Also can you supply the results of this terminal command ```
sudo fdisk -l
``` This should give us the size and disk label if indicated. How about as well  ```
df -h
```

---

### Post by Ron W on 2011-01-23
Hello MooPi

The following sizes are taken during a Clonezilla imaging sessions.

sda1 is 420 MB
sda2 is 125,030 MB
sda3 is 124,610 MB

The Toshiba restore files are on sda3, but I'll move these to sda2 (I have already saved these to DVDs should I need them, and if they are useful after the rearrangement).

Ron

---

### Post by MooPi on 2011-01-23
If your secure in your backup for Windows 7 then I'd say sda3 is a good candidate for Linux. You should be able to look at the contents of each drive if you use a Live CD or thumb drive. This way you can determine which drive has your Windows 7 install.

---

### Post by Gordonbp531 on 2011-01-23
The Windows 7 install will be on sda1......

---

### Post by Quackers on 2011-01-23
What does Windows disk management screen show?

---

### Post by Ron W on 2011-01-23
How do I get to the 'Windows disk management screen'?

---

### Post by Quackers on 2011-01-23
Start > right-click Computer and select "manage" then in the left pane of the new window select "disk management"

---

### Post by Ron W on 2011-01-23
It shows:

Volume with no name
Layout: Simple, Type: Basic, File System: <blank>, Status: Healthy(Active, Recovery Partition), Capacity: 400MB

Data (D: )
Layout: Simple, Type: Basic, File System: NTFS, Status: Healthy(Primary Partition), Capacity: 116.05GB

WINDOWS (C: )
Layout: Simple, Type: Basic, File System: NTFS, Status: Healthy(Boot, Page File, Crash Dump, Primary Partition), Capacity: 116.44GB

---

### Post by Quackers on 2011-01-23
It seems you have a 250GB hard drive. If there is nothing in D: it and you don't need that partition, it would be safe to delete that partition, leaving unallocated space for Ubuntu to install into.
An extended partition can then be created in that space, but I would do that with gparted, or with the Ubuntu installer.
However, it is quite common for Toshiba machines to need boot paramaters added to run the disc. I would advice trying the live cd desktop first. Then you can find out what parameters are required for installing and (later) running Ubuntu.

---

### Post by Ron W on 2011-01-23
I've already tried using the Ubuntu Live. Unfortunately, I'm having difficulty getting very far. I've tried the following:

1)
with computer turned off
put in flash drive.
turned on computer
pressed [F2]
moved the USB to the first item in the BIOS
saved and exited
result -
Get 'boot:' in top left hand corner
and the flash drive is turned off

2)
with computer turned off
put in flash drive
turned on computer
pressed [12] and got the 'Boot Menu'
USB is the top item and highlighted
Pressed enter
result -
Get 'boot:' in top left hand corner
and the flash drive is turned off

Do you have any suggestions of what to do?

---

### Post by Quackers on 2011-01-23
How did you burn the iso to the flash drive?

---

### Post by Ron W on 2011-01-23
I followed the instructions on

[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)

After trying the flash drive on the Toshiba, I tried in on my desktop PC and it loaded up okay, so I'm assuming that this stick is okay (but I could be wrong).

---

### Post by Quackers on 2011-01-23
Which version of Ubuntu are you using (10.04 or 10.10)
If it's working in the other machine it looks like a bios problem on yours.

---

### Post by Ron W on 2011-01-23
The version on my desktop PC is 10.04, and the version I'm trying to load on to the netbook and that is on the flash drive is 10.10.

---

### Post by Quackers on 2011-01-23
There is a Launchpad bug somewhere about Maverick and usb sticks and some difficulties iirc.
If you still have both the iso files you could try the 10.04 version on the usb. At least that might confirm where the problem lies.

---

### Post by Ron W on 2011-01-23
I'm getting a bit lost here.

I've copied the files from the 10.04 disk (that I'd prepared when I installed 10.04 onto my desktop PC) on to the flash drive (I put the 10.10 files in to a folder called 10.10 on the same flash drive).

I still get the same problem - 'boot:' in the top left hand corner and the flash drive being unmounted. When I press the enter key I get 'Could not find kernal image: linux'.

Does that give any clues?

---

### Post by Quackers on 2011-01-23
Did you use usb creator again?
I have a problem getting a usb to boot as well, but I think that's due to the firmware of the usb stick. When I connect my stick 2 new drives appear (instead of just one). Does yours do the same. by any chance?

---

### Post by Ron W on 2011-01-23
I've just found a netbook 10.04 version (ubuntu-10.04-netbook-i386.iso). I'm downloading it and then going to burn it using Brasero onto the flashdrive. However, would I have better if it was burnt on to a DVD?

---

### Post by Ron W on 2011-01-23
I've just put in the 10.04 LTS disc (that I used to install Lucid Lynx) in to the external DVD drive that I have connected to the netbook - and I've got in, so to speak. So it looks like that I can use the DVD drive.

I'm a bit confused though. If I burn the netbook iso file on to a DVD disc using Brasero, will Brasero burn the relevant files and folders onto the DVD (e.g. folders like 'casper', 'dists', 'install', etc)?

---

### Post by Ron W on 2011-01-23
Quackers

Following on from my previous post, I think that I understand that the iso file is like an image and contains all the files required, and Brasero 'knows' to put the files and folders on to the DVD rather than the iso file.

If I am correct, then my next main question is, as I've only one blank DVD, are there, to your knowledge any issues with the 10.10 netbook version that I need to know about before I use my last DVD up, or should I stick to the 10.04 version?

Thanks for all your help so far. It has been really appreciated.

Ron

---

### Post by Quackers on 2011-01-23
I have made 10.10 cd's without a problem. 
An iso file is an image of a cd and must be burned to disc (or usb) as an image, not as a file. There is usually a separate option for burning images. It's usually something like "burn image" or "burn iso" or something like that (believe it or not! :-)  )

---

### Post by Ron W on 2011-01-23
I've now made two CDs with 10.10 but both times I get the following at the top left hand corner of the screen:

graphics initialization failed
Error setting up gfxboot
boot:

It appears to keep trying to reboot as this appears to flicker.

However, I've tried 10.04 with much more success - I've actually got the Live version working. Now, to see what happens with the installation.

Again, thanks for all your help; it is really appreciated. I'm sure without it I would have given up.

Ron

---

### Post by Quackers on 2011-01-23
You're welcome :-)
Never give up!  Good luck :-)

---

