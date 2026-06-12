---
title: "I need urgent help: 10.04 broken in a Dell Mini 9"
date: 2010-06-11
forum: General Help
---

### Post by Newbie804 on 2010-06-11
Hi,
it was working fine.  Then when I tried to turn my Dell Mini 9 off it did not respond so I "forced" to turn it off with button.  Now it does not find the OS!
The only solution is to reinstall 10.04 netbook version again? (I'm downloading iso right now because I had already deleted it...)
Will some kind of "repair broken version" option appear when I try to install it?
And what about my docs?  I lost some docs when I installed 10.04 and uninstalle the original version 8.04... I do not want to lost them again!

Thanks for any help!

---

### Post by Newbie804 on 2010-06-12
Hi,
I'm still downloading iso file and waiting for some tips.
Thanks,

---

### Post by mechdave on 2010-06-12
What is the error message that you get?

---

### Post by Newbie804 on 2010-06-12
PXE-M0F: Exiting PXE ROM.
Operating System not found

---

### Post by xedth2 on 2010-06-12
Did you try going into the boot options on boot up and forcing it to look at the hard drive?

---

### Post by xedth2 on 2010-06-12
Also once you get the ISO downloaded you could run the live cd and look at your hard drive and make sure everything looks okay from there.

---

### Post by Newbie804 on 2010-06-12
> **xedth2 said:**
> Did you try going into the boot options on boot up and forcing it to look at the hard drive?
Humm  I do not know what is it or how to do it...
Sorry... :oops:

---

### Post by Newbie804 on 2010-06-12
> **xedth2 said:**
> Also once you get the ISO downloaded you could run the live cd and look at your hard drive and make sure everything looks okay from there.
Okay.
Thanks,

---

### Post by mechdave on 2010-06-12
Ok, the PXE bit means that the computer is looking for a boot image on the network. This is no good, what you need to do is to enter BIOS and get the computer to look for the hard drive instead. Whilst turning on the computer hold down the 2 key (I think) and it should take you into BIOS. There (hopefully you don't need to enter a password), you can change the boot order of your drives. Yo need the hard disk to be the first boot device. BE CAREFUL, anything you change in BIOS will affect your computer, you can't destroy anything but there are lots of things that can get screwed up :)

---

### Post by Newbie804 on 2010-06-12
> **mechdave said:**
> Ok, the PXE bit means that the computer is looking for a boot image on the network. This is no good, what you need to do is to enter BIOS and get the computer to look for the hard drive instead. Whilst turning on the computer hold down the 2 key (I think) and it should take you into BIOS. There (hopefully you don't need to enter a password), you can change the boot order of your drives. Yo need the hard disk to be the first boot device. BE CAREFUL, anything you change in BIOS will affect your computer, you can't destroy anything but there are lots of things that can get screwed up :)
Well,
I had changed before to prepare to use my pendrive... so I had choosen Boot Menu / Removable Devices

I enter the Boot Menu again:
Options:
*Hard Drive
CD/DVD/CD-RW
Removable Devices
Network Boot
Diagnosis

I mark Hard Drive, but it seems that it was already marked.

The same error:
It starts with something like

CLIENT MAC ADDR: 00 21 70 E7 3D 5F GUID: 20202020-2020-2020-2020-202020202020
PXE-E53: No boot filename received

PXE-MoF: Exiting PXE ROM.
Operating System not found

Thanks,

---

### Post by mechdave on 2010-06-12
Ok so what happens if you change it to say cdrom drive, try and boot and after it fails go back into boot menu and change back to hard drive? For some reason it is defaulting to network boot :-/

NOTE: Have a look at this video, it will help you out a lot --> [http://www.youtube.com/watch?v=mN0TkBWZZaY](http://www.youtube.com/watch?v=mN0TkBWZZaY)

---

### Post by Newbie804 on 2010-06-12
> **mechdave said:**
> Ok so what happens if you change it to say cdrom drive, try and boot and after it fails go back into boot menu and change back to hard drive? For some reason it is defaulting to network boot :-/
Okay,
I tried all boot options and the result is the same.
I also disconnected my cable.

It says PXE-E61: Media test failure, check cable
PXE...
Operating...

What happens is that no matter the option I choose and save everytime I enter the boot options it seems to me that hard drive is marked because there is an

* Hard Drive

???

---

### Post by mechdave on 2010-06-12
Look at this video and follow what it says, see which device in BIOS is first in the list. Make sure your network boot is last on the list --> [http://www.youtube.com/watch?v=mN0TkBWZZaY](http://www.youtube.com/watch?v=mN0TkBWZZaY)

---

### Post by Newbie804 on 2010-06-12
> **mechdave said:**
> Look at this video and follow what it says, see which device in BIOS is first in the list. Make sure your network boot is last on the list --> [http://www.youtube.com/watch?v=mN0TkBWZZaY](http://www.youtube.com/watch?v=mN0TkBWZZaY)
Okay,
I disable network and also
* in fact is + ups... just to expand to my HD

After reboot I receive a quick response:

Operating System not found
_

---

### Post by mechdave on 2010-06-12
You need to make sure hard drive is on top of the list

---

### Post by Newbie804 on 2010-06-12
> **mechdave said:**
> You need to make sure hard drive is on top of the list
Yes, it is...
I disable all other options (have an ! in front of every option but HD).
Also before I play and change orders, and save, and reboot, change again, reboot,...,
HD is the first and only option

Operating System not found

---

### Post by mechdave on 2010-06-12
Ok restart and boot up the live disk that you just downloaded and lets have a look at the hard drive...

Once it is booted up open a terminal and type ```
 sudo fdisk -l 
```
paste the result here :)

---

### Post by Newbie804 on 2010-06-12
> **mechdave said:**
> Ok restart and boot up the live disk that you just downloaded and lets have a look at the hard drive...

Once it is booted up open a terminal and type ```
 sudo fdisk -l 
```paste the result here :)

Okay.
but did not finish download... 
more 2h 22 minutes... 

I have to wait...

Sorry and thanks

---

### Post by mechdave on 2010-06-12
What did you do right before the system failed? Can you tell me the commands you used just before it stopped working?

---

### Post by Newbie804 on 2010-06-12
In fact it was my PC was slowly and there were 2 things:
#1 I thought it was because of Ubuntu One.  I had just subscribe (paid) this month and it seems to me it was always using some extra memory (many files are not back-up already...).  Then I tryed many times to desconnect (from Ubuntu One) and restart PC and it seems to me that it was always connected...
#2 There were about 8 or 10 fifes to be updated in the system yesterday.  So I repeat installing this system files many times because every time it said not all files were downlaoded... so I do not install all together but at the end it seems to me that all files were updated.

Then suddenly the systems appeared to freeze.. but not completely.  I tried many times to turn it off (ubuntu menu) but no response.  I close browse and some apps without problem.  I tried to start Skype again ( I use and I had closed it) but it said it was already running but no icon was showing its activity.

So as the system did not turn off I press the physical ON/OFF button.  I received a message saying that not all process had finished and asking confirming if I really want to turn off... so I click YES! and then...
the system did not work anymore...

Ups...

---

### Post by Newbie804 on 2010-06-12
BTW,
so Ubuntu does not have an option to Repair Installation if it detects a previous installation? Does it detect?

and also I found some information about Test Disk ([http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)).  Do you thing it could help me?

---

### Post by mechdave on 2010-06-12
Ok, from what I have been reading around the net people are having problems with the Dell Ubuntu. The fix would be to install the Ubuntu netbook remix from Ubuntu --> [http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)
As for the solution to your problem I do not know enough about what updates were being run at the time of failure. I suspect that the updates mis configured something with the bootloader. It may be far easier to just start again with the Ubuntu netbook remix and not the Dell Ubuntu...

The TestDisk is for Windows and not Ubuntu :(

---

### Post by Newbie804 on 2010-06-12
> **mechdave said:**
> Ok, from what I have been reading around the net people are having problems with the Dell Ubuntu. The fix would be to install the Ubuntu netbook remix from Ubuntu --> [http://www.ubuntu.com/netbook](http://www.ubuntu.com/netbook)
As for the solution to your problem I do not know enough about what updates were being run at the time of failure. I suspect that the updates mis configured something with the bootloader. It may be far easier to just start again with the Ubuntu netbook remix and not the Dell Ubuntu...
That is what was running and what I'm downloading again... 

> The TestDisk is for Windows and not Ubuntu :(
Well I downloaded a version to linux...

Thanks,

---

### Post by mechdave on 2010-06-12
You could try it but I would recommend care and reading the documentation first. :)

---

### Post by Newbie804 on 2010-06-12
I think I'm going to reinstall everything again.
I started Ubuntu from pendrive but I cannot access my HD.  I would like to copy some files but did not find a way to get my HD.  All what I found were directories from my pendrive...

---

### Post by Newbie804 on 2010-06-12
> **mechdave said:**
> Ok restart and boot up the live disk that you just downloaded and lets have a look at the hard drive...

Once it is booted up open a terminal and type ```
 sudo fdisk -l 
```paste the result here :)
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002fc23

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        3878     3908992+   b  W95 FAT32
ubuntu@ubuntu:~$

---

### Post by mechdave on 2010-06-12
It appears that the Mini 9 SSD hard drive is good at doing this, as yet I don't have a fix. but google reports the hard drive losing everything quite a lot :(

It seems that the Mini 9 hard drive breaks really easily... My advice is to ring Dell and get them to replace the hard drive for you. Here is the post from the Dell forums --> [http://en.community.dell.com/support-forums/laptop/f/3518/p/19241212/19371459.aspx](http://en.community.dell.com/support-forums/laptop/f/3518/p/19241212/19371459.aspx)

Or try and get a refund or credit on it for a different computer :)
Good luck and may the Linux gods smile upon you :)

A thought just occured to me, have you checked to make sure the hard drive is actuallt still plugged in to the computer? I am not sure if you can do that without too much trouble... maybe look on youtube for a tutorial video or something :)

---

### Post by Newbie804 on 2010-06-13
Please help!!
I decided to reinstall Ubuntu but I tried more than 10 times and it is not working...

I had already downloaded 3 times the iso file and had created USB flash about 6 times and tried installation about 10 times and always I get the error:

ERROR!!!
Input/output error during read on /dev/sda

Please help me!  More than 48 hours with this problem and without my netbook... :-(

---

### Post by mhgsys on 2010-06-13
Looks like a broken harddisk to me; 

That would explain why bios intends to boot from lan, ..even if disk is selected.
Bios will try all options.. and if no hd is working, and no cd is inserted, or no usb is plugged in.. leaving you the netboot.


2 bad; sometimes hd's break down, in fact I've got a old compaq laptop here myself with a failing hd; 

Saving op my money to buy  solid state disks instead.

Recommending you the same thing

edit: This is a ssd?? 
(according to mechdave)
> **mechdave said:**
> It appears that the Mini 9 SSD hard drive is good at doing this, as yet I don't have a fix. but google reports the hard drive losing everything quite a lot :(

It seems that the Mini 9 hard drive breaks really easily... My advice is to r**ing Dell and get them to replace the hard drive** for you. Here is the post from the Dell forums --> [http://en.community.dell.com/support-forums/laptop/f/3518/p/19241212/19371459.aspx](http://en.community.dell.com/support-forums/laptop/f/3518/p/19241212/19371459.aspx)



A thought just occured to me, **have you checked to make sure the hard drive is actuallt still plugged in to the computer?** :)

---

### Post by Newbie804 on 2010-06-13
Yes it is a solid state disk: Dell Mini 9.
[http://ubuntuforums.org/showthread.php?t=1508879](http://ubuntuforums.org/showthread.php?t=1508879)

---

### Post by mhgsys on 2010-06-13
I know; that's why I quoted mechdave)... and** bolded** his comment on the solution for you.

**have you checked to make sure the hard drive is actually still plugged in to the computer?**
[U]
when your sure it's plugged in ; and it's still not working[/U]

**ring Dell and get them to replace the hard drive**

I think They owe you that on a ssd..

edit: from [http://ubuntuforums.org/showthread.php?p=9456049#post9456049](http://ubuntuforums.org/showthread.php?p=9456049#post9456049)

> **Newbie804 said:**
> How to check it?


> **mhgsys]	

I don't know where dell "hides" their disks..

You should be able to locate some screws/plastics/slots on your laptop..

fe said:**
> 

[quote=mhgsys]Btw; I'm in a nice mood;..lol.;
Dell inspiron Mini 9 ?

**[http://www.youtube.com/watch?v=4H7NOO2AVkk[](http://www.youtube.com/watch?v=4H7NOO2AVkk[)**


---

### Post by Newbie804 on 2010-06-13
Okay, checked and it is its place.
BTW I must ask:
when running Ubuntu from pendrive (without installing) should I see my SSD?  Because I can't.  I only can find the pendrive (or I do not know how to find my SSD in my "folders and files").

---

### Post by mhgsys on 2010-06-13
Yes; if it wasn't broken you could see it ;
But it seems you already tried that with no succes.

 [quote= mechdave]  
Ok restart and boot up the live disk that you just downloaded and lets have a look at the hard drive...

Once it is booted up open a terminal and type
Code:

 sudo fdisk -l

paste the result here
[/quote]

[quote= Newbie804]
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sdb: 4002 MB, 4002910208 bytes
32 heads, 63 sectors/track, 3878 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002fc23

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 3878 3908992+ b W95 FAT32
ubuntu@ubuntu:~$ [/quote]

---

### Post by Newbie804 on 2010-06-13
Bad news...
:-(

---

### Post by Newbie804 on 2010-06-13
I just found this... almost the same problem... started with the skype issue...

[http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/17107-dell-mini-9-solid-state-drive-error-disk-read-error-occurred.html](http://www.mydellmini.com/forum/dell-mini-9-hardware-issues-problems/17107-dell-mini-9-solid-state-drive-error-disk-read-error-occurred.html)

---

