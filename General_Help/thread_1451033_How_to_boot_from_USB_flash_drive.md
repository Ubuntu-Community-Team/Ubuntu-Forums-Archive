---
title: "How to boot from USB flash drive"
date: 2010-04-09
forum: General Help
---

### Post by quadproc on 2010-04-09
Folks, I could use some ideas.  I am trying to use a Sandisk 2 GB USB flash drive to boot this system but the system is ignoring the drive.  The system boots fine from the CD or from the first hard disk.

Here are some details:
ASUS P6T SE mother board
Cooler Master HAF case
Ubuntu v 9.10 64 bit
Sandisk 2GB USB flash drive

I have plugged the flash drive into a convenient front panel USB connector, right next to where the floppy drive is plugged in.

I used the USB Startup Disk Creator to copy a disk file containing Ubuntu 9.04 Live CD onto the flash drive, then I used install-mbr on that drive.  I can use the usual tools such as nautilis to examine the contents of the flash drive, and for fdisk -l I get:

> Disk /dev/sdh: 2000 MB, 2000682496 bytes
64 heads, 63 sectors/track, 969 cylinders
Units = cylinders of 4032 * 512 = 2064384 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1   *           1         969     1953439+   6  FAT16which seems to say that the flash drive is bootable.

I am suspecting that the problem is in the mother board and/or BIOS.  The BIOS is set up to boot in the following order: CDROM, removable device, first hard disk.  I thought that "removable device" included USB drives but the system seems to ignore that drive.

There are lots of USB connectors in this system.  There is a keyboard, a mouse, a loudspeaker set, a floppy drive, and the aforementioned USB flash drive plugged into various USB connectors on  both the front and back sides of the cabinet.

Any suggestions for what to try?  Thanks.

quadproc

---

### Post by oldfred on 2010-04-09
The boot flag is just that and used by windows to know what partition to boot but grub does not use it. If you installed a boot loader to the MBR then it should boot.
On my PC it says it can boot from USB and lists lots of things like USB-floppy, USB CD,USB etc. But it would not boot. One day I had the USB key in and happened to use F12 to choose a different hard drive and there was my USB key under hard drives. Check your hard drive list with the key plugged in.

---

### Post by quadproc on 2010-04-10
> **oldfred said:**
> The boot flag is just that and used by windows to know what partition to boot but grub does not use it. If you installed a boot loader to the MBR then it should boot.
Thanks for the reply.  I am still stuck but I do know some more now so please let me update the situation.

Examining the USB drive I found that there was no _boot_ directory on it.  This was after I used the 9.10 USB Startup Disk Creator which the literature says does everything necessary.  I do find the following on it now:

>  ls -la
total 133028
drwx------ 11 bob  bob      16384 2010-04-10 14:27 .
drwxr-xr-x  6 root root      4096 2010-04-10 13:24 ..
-rwxr-xr-x  1 bob  bob        143 2010-04-10 13:18 autorun.inf
drwx------  2 bob  bob      32768 2010-04-10 13:18 casper
-rwxr-xr-x  1 bob  bob  134217728 2010-04-10 13:19 casper-rw
drwx------  2 bob  bob      32768 2010-04-10 13:18 .disk
drwx------  3 bob  bob      32768 2010-04-10 13:18 dists
drwx------  2 bob  bob      32768 2010-04-10 14:32 grub
drwx------  2 bob  bob      32768 2010-04-10 13:18 install
-r-xr-xr-x  1 bob  bob      14607 2010-04-10 13:18 ldlinux.sys
-rwxr-xr-x  1 bob  bob       4794 2010-04-10 13:18 md5sum.txt
drwx------  2 bob  bob      32768 2010-04-10 13:18 pics
drwx------  4 bob  bob      32768 2010-04-10 13:18 pool
drwx------  2 bob  bob      32768 2010-04-10 13:18 preseed
-rwxr-xr-x  1 bob  bob        229 2010-04-10 13:18 README.diskdefines
drwx------  2 bob  bob      32768 2010-04-10 13:18 syslinux
-rwxr-xr-x  1 bob  bob    1533687 2010-04-10 13:18 wubi.exe
I believe that I was able to copy the relevant things over to the USB drive to install grub on it, except that when I got to the menu.list portion I could not figure out how to get the UUIDs nor the version numbers of the release(s) that I want to store on the USB drive(s).  So I omitted the menu file, hoping that grub would default to safe and sane assumptions.  But when I tried to boot from this arrangement, I still saw no indication whatsoever that the USB drive was ever tried by the BIOS.

The USB drive seems to work fine as a filesystem - I can copy things to it, read files from it, check its properties, etc.

I am guessing that either 1) The BIOS is not trying the "removable device", or 2) The grub installation is not correct.  I spent some time with grub, trying to use it to install itself onto the USB drive, but got stuck doing that when I tried to use its "find" command on the _stage1_ file and could not find it.  Without guaranteeing that I was on the right disk and partition, I was unwilling to do an MBR install.

Comments, suggestions, even guesses are welcome.  Thanks.

quadproc

---

### Post by sgosnell on 2010-04-10
When the BIOS flash screen comes up during the initial boot process, press Esc, then select the USB drive.  If the drive is actually bootable, it should boot.  If it won't, you don't have a bootable drive, and need to reinstall Ubuntu to it.

---

### Post by oldfred on 2010-04-10
You have a syslinux install which does not use grub.
My USB looks just like yours but boots from a hard drive selection with f12.

---

### Post by quadproc on 2010-04-11
> **oldfred said:**
> You have a syslinux install which does not use grub.
My USB looks just like yours but boots from a hard drive selection with f12.
Interesting.  I think that that means a couple of things: 1) the Ubuntu USB Startup Disk Creator did not install anything for booting, and 2) syslinux is not being executed.

I have tried experimenting with various keyboard inputs during the boot process.  When I did this, I tried DEL, F2, F10, and F12.  I input the character at least once while the BIOS's initial timeout is counting down.  When I use a function key, the countdown stops so I know that the BIOS saw the keystroke.  When I use the DEL key then the BIOS switches into setup mode.  At that point the BIOS is not giving me a way to specify where to boot from but I can get to the boot device order screen and check to see that "removable devices" are before the hard disk.  When I exit the BIOS setup screen then the system presents the usual grub menu which contains three different releases, their recovery mode entries, and a couple of memtests.  Then I can either wait for the boot countdown, hit RETURN to cause immediate boot, or use the miscellaneous functions such as edit.  At this point the system will only boot one of the selections from the grub menu, and there is no selection for the USB drive.

I obtained the boot info script from sourceforge and ran that on this system with the USB drive plugged in. For this experiment the system has assigned the USB drive to /dev/sdh.  Here is a bit of what it reported:
> => Syslinux is installed in the MBR of /dev/sdh
...
sdh1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Fat32
    Boot sector info:  According to the info in the boot sector, sdh1 starts 
                       at sector 0. But according to the info from fdisk, 
                       sdh1 starts at sector 63.
    Operating System:  
    Boot files/dirs:   Drive: sdh ___________________ _____________________________________________________

Disk /dev/sdh: 2000 MB, 2000682496 bytes
255 heads, 63 sectors/track, 243 cylinders, total 3907583 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x000c7850

Partition  Boot         Start           End          Size  Id System

/dev/sdh1    *             63     3,903,794     3,903,732   6 FAT16
...
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        26AE4A30AE49F937                       ntfs                                     
/dev/sda5        b92fb3a5-c503-4168-a61f-7e6ea6661a0a   ext3                                     
/dev/sda6        b0b35cc7-895a-456e-8a3c-af1fd8457a7e   swap                                     
/dev/sda7        df533fe8-68c3-41f6-b030-e955feb580d9   ext3                                     
/dev/sda8        b071f4d5-5384-4267-9f78-99e163d6ea4a   swap                                     
/dev/sdb5        ae2cdad8-459c-4692-908d-eea07cd1fe9b   ext3                                     
/dev/sdb6        a7d2d1fc-dd54-4226-b4fd-f9c145f319a4   swap                                     
/dev/sdc1        F4EE44F4EE44B122                       ntfs                                     
/dev/sdh1        CBB5-FD78                              vfat       9816-8f19                     
...
=================== sdh1: Location of files loaded by Grub: ===================


    ??GB: grub/stage2
=======Devices which don't seem to have a corresponding hard drive==============

sdd sde sdf sdg 

...The item regarding where things start in /dev/sdh concerns me but I don't know why things ended up that way, or what I should do about it.

Now, it looks like I could try to get syslinux working or I could try to install grub on the USB drive and point that to the OS on that drive.  Comments, suggestions, ideas are all welcome.  Thanks.

quadproc

---

### Post by oldfred on 2010-04-11
The installs using grub seem to want at least a 4GB USB key as the full install takes more space. The syslinux installs or the booting ISOs work from 2GB keys.

Another ISO boot link:
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)

And a bunch of links I saved:
How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the ccaveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by quadproc on 2010-04-11
> **oldfred said:**
> The installs using grub seem to want at least a 4GB USB key as the full install takes more space. The syslinux installs or the booting ISOs work from 2GB keys.
Interesting.  So far, I have not seen any complaints about the flash drive getting full.  Checking the drive with df gives /dev/sdd1              1951584    849440   1102144  44% /media/9816-8f19
I figured that since everything that I needed was on a 700 MB CDROM that a 2 GB drive would be sufficient.  Next time I get to the local computer store I will get a bigger one.  Meanwhile, I have been trying various things and have learned two very important things: grub's find command does not work, and I can work around that by using grub's geometry command.  All that I was after was knowing for sure which device designation I needed to tell grub.  It turns out that grub only recognizes the "hda" identifiers even though the system assigns them "sda" identifiers.

Once I was confident that I could specify the correct drive, I used the grub commands of root and setup.  Those succeeded.  Then I made a menu.lst file but here I had a problem: I do not know what the system will think the UUID of the flash drive is when it is being booted so I don't know how to create the menu file.  So I tried this:
> title        Ubuntu 9.04, kernel presently unknown 4/11/10
##uuid        9816-8f19
kernel        /casper/vmlinuz ro quiet splash lang=us
initrd        /casper/initrd.gz
quietwhich did not work.  I am not sure, but it might have taken longer than usual for the bootup sequence to execute.  If true then that would suggest that things got a little farther along before the BIOS gave up and went to the next entry in its list, namely the first hard disk.

I am beginning to wonder if it is possible to boot from a USB device on this system.  The mother board uses an Intel ICH10 chip and a JMicron somethingorother to get to the peripherals.  I think that some kind of a driver is required to allow the USB things to function, but that driver may have to be loaded by the OS.  If that is true then my effort is futile.  But perhaps the BIOS provides some kind of a driver for startup purposes; the documentation is silent on this subject.
> 
Another ISO boot link:
 HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2 
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604)

And a bunch of links I saved:
How to install ubuntu on USB drive and carry entire computing system in pocket? 
[http://ubuntuforums.org/showthread.php?t=789528](http://ubuntuforums.org/showthread.php?t=789528)
With details on some of the ccaveats, std install.
[http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html](http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)Thanks for the library!  I will do some studying.

quadproc

---

### Post by sgosnell on 2010-04-11
If you just make an install disk, 1GB will work.  If you actually do a full install to the disk, you need more room.  4GB will work, 8GB is better.  What I like to do is use 2 USB drives, one 1GB, the second bigger, and boot from the small one with the install program on it, then do a full install to the big one.  That lets me carry a full OS on a stick, on which I can have my full /home and the full suite of packages ready to go.  I can have my usual Ubuntu system available on any computer I come across.  The disk you get from the process you're using does little beyond install Ubuntu on another drive.  It can run, and can save some data, but it's not a full-blown OS for daily use.

---

### Post by DawieS on 2010-04-11
I have today used a 1 GB (965 MB) flash-drive to create a bootable USB drive for an Ubuntu installation. With my first try it did not boot up correctly from the flash drive. What I then did was (using GParted):

- Created 2 partitions on the flash drive, the first one being very small (39.2 MB), (rounded to nearest cylinder), and the second one the rest of the drive.

- Deleted the first partition (leave as unallocated space) and format the second partition to FAT32. Also mark flags boot and lba.

- Used UNetbootin to create a bootable usb drive from a downloaded iso Ubuntu distro.

I think the unallocated space is used for writing the boot loader information to be able to successfully boot from the flash drive. On my machine I have to first insert the flash drive into a USB port and then boot up, pressing delete to enter the BIOS settings. The boot sequence is selected as HDD-USB first. I have then successfully installed Ubuntu on another machine (without a CD ROM drive).

---

### Post by quadproc on 2010-04-12
> **sgosnell said:**
> If you just make an install disk, 1GB will work.  If you actually do a full install to the disk, you need more room.
What I am hoping to do is the equivalent of a Live CD - something that I can plug into the computer, do a restart, and be running an arbitrarily old version of Ubuntu.  If I can get that to work then perhaps I will do a fully installed system on a stick.

Meanwhile, I decided to try out the very well written instructions at [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604).  The procedure went well and did not report any problems, but I noticed that there was no boot flag indicated for the USB drive so I went back with gparted and added one.  Even so, there was no indication that this system tried to boot from the USB drive.

Has anyone else used an ASUS P6T SE and gotten the USB drive to boot?  If so, what kind of USB drive did you use?  Thanks.

quadproc

---

### Post by oldfred on 2010-04-12
My motherboard is a gigabyte, but I was just creating a USB for the Lucid beta using the USB startup creator but I had another data USB plugged in as I was not sure which was which. When I tried booting it would not work. I unplugged the data USB and then it booted.

Do you have another USB key plugged in?

---

### Post by quadproc on 2010-04-12
> **oldfred said:**
> 
Do you have another USB key plugged in?
That is good thinking but no, the only plugged in USB flash memory is the one that I am trying to boot from.  There are lots of other plugged in USB devices such as mouse, keyboard, loudspeakers, and UPS.  I have unplugged the USB floppy while doing these experiments.

I have learned some more things in the meanwhile.  It seems that I have grub version 0.97 on both the usual hard disk install and on the USB drive, even though the article from JustRon indicated that grub2 (aka grub-pc, I believe) would be installed.  Since I have the original grub it will need a menu.lst file so I made one by trimming down my standard system boot menu.  This also fails to do anything.

One thing that I noticed during the startup sequence is that, after the BIOS hands things off to the boot software, I see a very brief (maybe 2/10 of a second) message at the top of the screen and it says something about grub.  But it is a few lines long and it lasts so little time that I can't read what it says.  I'll bet that there is something useful in it but I don't know how to capture it.

Tantalizing but frustrating

quadproc

---

### Post by sgosnell on 2010-04-12
Exactly what are you doing during the boot process?  You should press Esc when the BIOS screen appears, then selecting the USB drive.  You may have to change the boot settings in the BIOS, but I don't know what you have set there now.  You probably need to make sure the USB drive is listed in the boot section, if you haven't already done that.  I'm still not completely clear on everything you've done, or how.

---

### Post by quadproc on 2010-04-12
> **sgosnell said:**
> Exactly what are you doing during the boot process?
OK, I have good news.  I contacted ASUS (the motherboard manufacturer) and asked them what a removable device is.  The first person that I spoke with said it was only a floppy.  I didn't believe this and got transferred to a second person.  The second person told me that yes, a removable device could be a floppy or a USB flash drive.  He said to press F8 during startup.  This is completely undocumented but it works!  It brings up a display of several possible boot devices and allows choosing one.  The choices include the USB flash drive.  The BIOS display is a little buggy in that it shows some entries twice, but at least it worked on the one of most interest to me. Selecting that brings me to the grub menu from the USB flash drive, and from there I can select an entry and boot with that.

This means that the writeup from JustRon [http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1288604) does work, provided that you also set the boot flag.

It probably means that the Ubuntu USB Startup Disk Creator works; I will have to try it out again.

It also means that you guys helped a lot, and that I learned a bunch from this experience.  Thanks to you all.

Now I have a new problem.  I programmed the USB drive to use the iso file of my Ubuntu 9.04 Live CD and it starts up without crashing but it brings up the wallpaper and the familiar splash and login screen from the 9.10 release and it does not present me with a cursor so I have no idea where it thinks that the mouse is.  Of course, this prevents me from doing anything but logging in.  I can kill X with control-alt-backspace but that just gets me back to the login screen.  So I have more research to do, and perhaps another thread to start.

Marking this thread as solved, and offering best regards.

quadproc

---

### Post by sgosnell on 2010-04-12
You may have a faulty OS install on the USB drive.  It's not unusual.  I would try doing the Make USB Boot Drive over from scratch.

Glad you got the original problem sorted out.  The usual way to get the device menu is with Esc, but it appears your BIOS is different.

---

