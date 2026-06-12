---
title: "Thumb drive, transfering files to Windows"
date: 2006-05-07
forum: General Help
---

### Post by John Jason Jordan on 2006-05-07
Ubuntu-64 Breezy on my laptop; Sandisk Cruzer 512 MB thumb drive. Computers in the computer lab at university run Windows XP.

I was at the university and needed to print out a document created in OpenOffice.org Writer. I exported to PDF, stuck the thumb drive in a USB port, and copied the file to the thumb drive. Then I went to the computer lab where they have banks of computers, all of which will print to a couple of big-*** lasers in the lab. I put the thumb drive in the USB port of one of the computers, logged in to my student account, and expected to open the PDF file and send it to the laser printer. But Windows Explorer saw only a file named reglog.txt -- no PDF file. After much fumbling around I gave up. I was in a hurry, so I just booted my laptop sitting on a chair next to me, e-mailed the file to my university e-mail account, then opened it from there and printed it.

Now I have been home for 24 hours and still cannot get a Windows computer to find the PDF file on the thumb drive. I have a Windows 2000 desktop and it acts exactly like the computers at the university -- it sees a file named reglog.txt, but no PDF file.

Reglog.txt exists on my Windows 2000 desktop. I have no idea how that file got onto the thumb drive, as the thumb drive has never been mounted on my desktop before today. Yet it is there. No question about it. While at the university I used Notepad to view what was in reglog.txt, and the contents were identical to the reglog file on my Windows 2000 desktop computer. The contents consist of a paragraph or so of tags, some of which have data in them, like my username on an e-mail account. (Nothing security sensitive, but definitely stuff that was on my own computer(s).)

With the thumb drive mounted on the Ubuntu laptop the PDF file is plainly visible. I can open it with PDF Viewer and send it to my home laser printer. It's definitely there. At the same time, Linux cannot see the reglog.txt file on the thumb drive.

The thumb drive is SDA and it has one partition, SDA1. Looking at it with Konqueror, Nautilus, Krusader and Endeavour, the reglog file is not there, and the PDF file *is* there. Looking at the drive with a Windows computer the PDF file is not there, but the reglog.txt file is there.

Why is the reglog.txt file invisible to Linux?

Why can't the Windows computers see the PDF file?

Oh, and I verified that the thumb drive is FAT32.

I've spent hours trying to figure this one out. Any suggestions welcome!

---

### Post by aysiu on 2006-05-07
Have you tried enabling hidden files in Windows and Ubuntu?

---

### Post by John Jason Jordan on 2006-05-07
[QUOTE=aysiu]Have you tried enabling hidden files in Windows and Ubuntu?[/QUOTE]
Yes, Show Hidden Files has always been enabled on my Windows 2000 desktop, but I just double checked and it is still enabled. It is also enabled in all my file managers on the Ubuntu laptop.

I just did another test. Previously the problem was that Windows computers (mine and at the computer lab at the university) were unable to see the PDF file that I placed on the drive from the Ubuntu laptop. And the Ubuntu laptop was unable to see reglog.txt, which must have been placed there by my Windows desktop, although when and why baffles me. The file date on reglog.txt is October 25, 2005, before I even owned the thumb drive.

So just now I placed a couple more random files on the thumb drive from the Ubuntu laptop and moved it to my Windows desktop. Windows still can't see anything but reglog.txt. And while it was on the Windows desktop I copied several random files to it from the Windows desktop, then moved it back to the Ubuntu laptop. Ubuntu still can't see anything but the files it put on the thumb drive, and Windows can't see anything but the files it put on the drive.

At least now I have a clearer picture of the problem. I just don't know why it is happening.

---

### Post by aysiu on 2006-05-07
I would consider reformatting the thumb drive. Something's clearly wrong. I've used FAT16 and FAT32 USB drives (USB sticks, my wife's iPod shuffle, my own Sandisk MP3 player) and transferred files between Ubuntu and Windows and Ubuntu and Mac OS X, and I've never encountered this problem.

Not only have I never encountered it myself, but I've never read (well, before your post) about anyone else on these forums having this problem.

You can format the drive in Windows by going to Disk Management (I forget what sub-menu it's under).

---

### Post by John Jason Jordan on 2006-05-07
[QUOTE=aysiu]I would consider reformatting the thumb drive. Something's clearly wrong. I've used FAT16 and FAT32 USB drives (USB sticks, my wife's iPod shuffle, my own Sandisk MP3 player) and transferred files between Ubuntu and Windows and Ubuntu and Mac OS X, and I've never encountered this problem.

Not only have I never encountered it myself, but I've never read (well, before your post) about anyone else on these forums having this problem.

You can format the drive in Windows by going to Disk Management (I forget what sub-menu it's under).[/QUOTE]
Thanks for the suggestion. I was just arriving at the same idea myself. Using the Windows desktop (because I couldn't figure out the mkfs command in Linux) I formatted it FAT32 with Disk Administrator. Then I unmounted it and moved it to the Linux laptop.

Guess what? Linux still sees all the files on it that I put on it previously from the Linux computer. Now, this is clearly impossible. So something tells me I have just discovered that the problem is on the Linux computer. It's not reading it correctly. And if it's not reading it correctly, then it's probably not writing to it correctly either. And that would explain why the Windows computer doesn't see the files I put on it from the Linux computer -- because they really were never there.

So, thinking maybe it's not being mounted, I opened Krusader, only to discover that it's not even listed in Mount Man (it's mount utility). From a command line I typed "mount" and got:

/dev/hda2 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-9-amd64-generic/volatile type tmpfs (rw,mode=0755)
/home on /chroot/breezy/32bits/home type none (rw,bind)
/tmp on /chroot/breezy/32bits/tmp type none (rw,bind)
/dev on /chroot/breezy/32bits/dev type none (rw,bind)
/proc on /chroot/breezy/32bits/proc type proc (rw)
/usr/share/fonts on /chroot/breezy/32bits/usr/share/fonts type none (rw,bind)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)

I'm not very good with Linux, so I don't understand most of that, but it doesn't appear that it is listed as mounted. It should be /dev/sda or something like that.

So how do I mount it?

---

### Post by aysiu on 2006-05-07
Mount it the same way you'd mount any FAT partition or disk:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.ubuntuguide.org/#automountfat](http://www.ubuntuguide.org/#automountfat)

---

### Post by rowanparker on 2006-05-07
Hello,
When I first got my flash drive I had exactly the same problem.

It happened when I just took the drive out without unmounting it first. You must (on desktop) right-click and unmount. Then it worked for me.

Although I formatted it using GParted first, don't know whether that made a difference.

Hope that helps, Rowan.

---

### Post by John Jason Jordan on 2006-05-07
[QUOTE=aysiu]Mount it the same way you'd mount any FAT partition or disk[/QUOTE]
OK, I managed to get it mounted. And I put two files on it to test it on my Windows desktop. But now I can't get it unmounted. All I get is "the device is busy." It's /dev/sdb1 and the commands I used are sudo umount /media thumbdrive (the mount point) and sudo umount /dev/sdb1. Same error message either way. I also tried using Krusader, a GUI file manager that has a mount/unmount utility. It sees it as mounted, but when I click to unmount it (running Krusader as root) it gives me the same "the device is busy" error message.

So how do I "unbusy" it?

---

### Post by John Jason Jordan on 2006-05-07
[QUOTE=rowanparker]Hello,
It happened when I just took the drive out without unmounting it first. You must (on desktop) right-click and unmount. Then it worked for me.[/QUOTE]
Yeah, I'm figuring this out. Right now it is mounted, but I can't get it unmounted. I don't use Nautilus, so there are never icons on my desktop. (Which I actually prefer.) But everything I have tried just gives me "the device is busy" error messages.

I need to get this figured out so I can mount and unmount it quickly and reliably. It would be nice if it would auto-mount, but I can live with having to mount and unmount manually. I just need to get it to WORK. My sole reason for having the thumb drive is to transfer files to a Windows computer in the computer lab at the university so I can print something out. Invariably this is going to be some homework that I needed to make last minute changes to and I'm going to be doing this like five minutes before class time. I can't deal with error messages that take days to figure out. 

Thanks for the suggestions so far.

---

### Post by John Jason Jordan on 2006-05-07
[QUOTE=John Jason Jordan] ... everything I have tried just gives me "the device is busy" error messages.[/QUOTE]
Finally got it figured out. I needed a "lazy" unmount. The command that finally worked was "sudo umount -l /dev/sdb1." That got it unmounted. Afterwards I moved it to my Windows desktop and Windows happily saw the files I put on it with the Linux computer. Problem solved, detailed instructions to myself saved in my CheatSheet file for next time this happens.

Thanks to all for the suggestions.

---

### Post by aysiu on 2006-05-07
[QUOTE=John Jason Jordan]Problem solved,[/quote] Glad it worked out for you, finally. > detailed instructions to myself saved in my CheatSheet file for next time this happens. Would you mind posting those instructions here in case someone else has this same problem and finds this thread?

---

### Post by John Jason Jordan on 2006-05-07
[QUOTE=aysiu]Glad it worked out for you, finally.  Would you mind posting those instructions here in case someone else has this same problem and finds this thread?[/QUOTE]
Actually, it turned out all I needed to note was the proper mount and unmount commands --

sudo mount -t vfat /dev/sdb1 /media/thumbdrive
sudo umount -l /dev/sdb1

Plus a note to myself to run "mount" and make sure it is not listed as mounted before pulling it out. 

The "-l" in the umount command is for "lazy," required because for some reason Linux thinks the thumb drive is busy and won't let me unmount it. The -l tells it to unmount it anyway and to hell with whatever program thinks it's using it.

---

