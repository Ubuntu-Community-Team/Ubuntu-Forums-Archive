---
title: "Boot time"
date: 2009-12-20
forum: General Help
---

### Post by nishant.singh28 on 2009-12-20
I am running Karmic 64 bit on my Dell Laptop( Specs in signature ). I want to reduce my boot time to as low as possible. I have already removed most of the unnecessary startup programs so no further cuts are possible there. I have noticed that the system takes most of the time mounting partitions. It waits for some time at:

One or more of the disks in /etc/fstab can't yet be mounted
press ESC to enter recovery shell......

Then the CD drive spins up after a dozen or two seconds and the system continues.

I use lmsensors, imwheel & hddtemp frequently so they are in startup. Also, I have a 250 GB portable hdd connected always to a USB port and have been advised by Dell to keep a cd in my optical drive to prevent dust from settling in and damaging it as it is a slot load.
I mount two internal partitions: an ext3 and an NTFS partition at startup. One holds some important data and the other, all my download folders. Now what do I do to reduce boot time?

---

### Post by TheOnlyMrK on 2009-12-20
Have you enabled Quick Boot and set your hard drive as the only media to try to boot from in BIOS? That's about all I can suggest right now, for me on my desktop that took about 10seconds off of it's boot.
On another computer I have I too am trying to tune a computer to run Xubuntu faster but more for reasons of the computers limitations. (500Mhz CPU, 272MiB RAM)

---

### Post by arrange on 2009-12-20
What's your bootup time then?

[COLOR="Silver"]One or more of the disks in /etc/fstab can't yet be mounted
press ESC to enter recovery shell......[/COLOR]
Can you post the appropriate section of *dmesg*, if you can find it?

Have you got *ureadahead* installed and functional?

---

### Post by nishant.singh28 on 2009-12-21
> **arrange said:**
> What's your bootup time then?

[COLOR=Silver]One or more of the disks in /etc/fstab can't yet be mounted
press ESC to enter recovery shell......[/COLOR]
Can you post the appropriate section of *dmesg*, if you can find it?

Have you got *ureadahead* installed and functional?
Approx a minute and half....
The disks in fstab get mounted anyway...
What part of dmesg should I post? ( The output is almost 4 pages long )
What is ureadahead and what does it do? ( I'm currently on a DSL link with a free download limit that is already exceeded so I don't want to risk destabilising my system. Will go unlimited in a couple of weeks )

---

### Post by nishant.singh28 on 2009-12-21
> **TheOnlyMrK said:**
> Have you enabled Quick Boot and set your hard drive as the only media to try to boot from in BIOS? That's about all I can suggest right now, for me on my desktop that took about 10seconds off of it's boot.
On another computer I have I too am trying to tune a computer to run Xubuntu faster but more for reasons of the computers limitations. (500Mhz CPU, 272MiB RAM)
I am not concerned with hardware testing time as it is ok with me.....I was talking about the time taken after grub screen to the login screen. And take a good hard look at my hardware specs before talking about "hardware limitations". I barely see 100% CPU usage or above 30% RAM usage, even while watching a 720p movie while burning a DVD at around 7x speed.

---

### Post by nishant.singh28 on 2009-12-21
Bump!

---

### Post by TheOnlyMrK on 2009-12-21
> **nishant.singh28 said:**
> I am not concerned with hardware testing time as it is ok with me.....I was talking about the time taken after grub screen to the login screen. And take a good hard look at my hardware specs before talking about "hardware limitations". I barely see 100% CPU usage or above 30% RAM usage, even while watching a 720p movie while burning a DVD at around 7x speed.

I was only using it as an example, if you look at my signature you can see that our computers are pretty equally matched. I was just saying you can/will save on boot up time if you adjust your BIOS properly. Example being their is no need to have it scan all your CD drives, USB drives, and hard drives for something to boot from when you can just select only your hard drive and when you need to boot from something else you press whatever button it is (F11 for me) to bring up the boot menu. As far as quickening up your boot the only suggestion I have is spend 2hours in Syniptic and uninstall everything you can find that you don't need. I did it, I could of been more through but I didn't want it to be a day long job, and it sped up everything, but not drastically.

---

### Post by nishant.singh28 on 2009-12-23
Man....don't compare your rig with a laptop and humiliate the poor thing...:D...anyway..I have done a lot of clean up already. It is just that I am irritated by the fact that the system gets stuck for some time at the message I posted above and then boots. So the million dollar question: HOW DO I PREVENT THE SYSTEM FROM READING AND MOUNTING THE CD IN MY OPTICAL DRIVE EVERY TIME IT STARTS????

---

### Post by nishant.singh28 on 2010-01-08
Bump!!!

---

### Post by nishant.singh28 on 2010-01-15
Bump!!

---

### Post by john newbuntu on 2010-01-15
Can you post your /etc/fstab please?

---

### Post by nishant.singh28 on 2010-01-15
```
# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                                       /proc             proc     defaults               0  0  
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=0c0516c7-8f8c-4c0c-93cf-5d3e02462fee  /                 ext4     errors=remount-ro      0  1  
# Entry for /dev/ !! UNKNOW DEVICE !! :
UUID=20c8c9ef-7275-46e8-8e83-a2211ba0904d  none              swap     sw                     0  0  
/dev/sda3                                  /media/Data       ntfs-3g  defaults,locale=en_IN  0  0  
/dev/sda2                                  /media/Downloads  ext3     defaults,users         0  0  
```

---

### Post by nishant.singh28 on 2010-01-15
> **nishant.singh28 said:**
>  So the million dollar question: HOW DO I PREVENT THE SYSTEM FROM READING AND MOUNTING THE CD IN MY OPTICAL DRIVE EVERY TIME IT STARTS????
And what about this? Also some errors about some inaccessible devices also comes up. I'll try to get a pic if needed here. But the funny thing is all my hardware, each and every bit of it works fine. None of the devices is inaccessible on the running system.

---

### Post by john newbuntu on 2010-01-16
Can you also list the output of "sudo blkid".

---

### Post by nishant.singh28 on 2010-01-16
```
/dev/sda1: UUID="D48064078063EF04" LABEL="System Reserved" TYPE="ntfs" 
/dev/sda2: LABEL="Downloads" UUID="ea9e062d-8295-4019-9459-007d09d4b651" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda3: UUID="2C783E18783DE16E" LABEL="Data" TYPE="ntfs" 
/dev/sda5: UUID="8c8ac2bc-bbf2-4911-b224-b529c22d1b98" TYPE="swap" 
/dev/sda6: UUID="2cf96e3e-3f87-494e-a104-f9dcf154aa0d" TYPE="ext4" 
/dev/sdb1: UUID="5AD4063ED4061CBF" LABEL="Nishant's Portable" TYPE="ntfs" 
```

---

### Post by nishant.singh28 on 2010-01-16
OK. So it appears to be a mismatch in the UUID. DO I need to change the UUID's in fstab or simply remove the two entries?

---

### Post by john newbuntu on 2010-01-16
First make a backup of the existing /etc/fstab (Very important) and then replace it with this one and see if it is any better.  Remember to leave the last line blank.  If you need /dev/sda3 later, uncomment that.

```
# /etc/fstab as of 1/16/10: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc                /proc             proc defaults           0  0

# Entry for /root
UUID=2cf96e3e-3f87-494e-a104-f9dcf154aa0d  /  ext4 errors=remount-ro  0  1

# Entry for swap at /dev/sda5
UUID=8c8ac2bc-bbf2-4911-b224-b529c22d1b98  none     swap     sw 0  0

#/dev/sda3           /media/Data       ntfs-3g defaults,locale=en_IN  0  0
/dev/sda2           /media/Downloads  ext3 defaults,users         0  0


```

---

### Post by nishant.singh28 on 2010-01-16
I backup my entire system every sunday. SO I'll try this after that. Thanks anyway.

---

### Post by sliketymo on 2010-01-16
> **nishant.singh28 said:**
> Man....don't compare your rig with a laptop and humiliate the poor thing...:D...anyway..I have done a lot of clean up already. It is just that I am irritated by the fact that the system gets stuck for some time at the message I posted above and then boots. So the million dollar question: HOW DO I PREVENT THE SYSTEM FROM READING AND MOUNTING THE CD IN MY OPTICAL DRIVE EVERY TIME IT STARTS????

Take the cd OUT of the drive.

---

### Post by nishant.singh28 on 2010-01-16
> **sliketymo said:**
> Take the cd OUT of the drive.
Not an option(Don't ask why). Any other ideas?

---

### Post by nishant.singh28 on 2010-01-16
> **nishant.singh28 said:**
> Not an option(Don't ask why). Any other ideas?
OK. you have a better idea to keep a slot load drive clean and prevent dust from going in? The Dell people recommended it. Anyone has a better idea, please tell me...

---

### Post by nishant.singh28 on 2010-01-16
First things first. A HUUUUUUUUUUGE thanks to john newubuntu for the fstab file. It cut my boot time into almost half. And the system's performance after the boot also seems to be a lot more snappier. One small issue though. I had said something about some errors a couple of posts back. I got a pair of photos of the error screen but it stays on momentarily so it's not easy to get a good pic. Please try to figure out what the error is.

---

### Post by nishant.singh28 on 2010-01-16
```
nishant@Nishant-Studio:~$ sudo ureadahead
[sudo] password for nishant: 
ureadahead:/usr/lib/bonobo/servers/GNOME_PilotApplet.server: No such file or directory
ureadahead:/usr/lib/bonobo/servers/GNOME_Pilot_Daemon.server: No such file or directory
ureadahead:/home/nishant/.local/share/gvfs-metadata/home-8085def9.log: No such file or directory
ureadahead:/home/nishant/.local/share/gvfs-metadata/uuid-2C783E18783DE16E-af67c02d.log: No such file or directory
ureadahead:/usr/share/dbus-1/services/gnome-org.freedesktop.PolicyKit.AuthenticationAgent.service: No such file or directory
ureadahead:/usr/share/dbus-1/services/org.gnome.PolicyKit.service: No such file or directory
ureadahead:/usr/share/dbus-1/services/org.gnome.PolicyKit.AuthorizationManager.service: No such file or directory
```
What is this supposed to mean?

---

### Post by nishant.singh28 on 2010-01-16
Sorry if I sound a bit too eager. I'm pretty new out here and have a lot of doubts. You see, I've used Windows for almost 14 years before switching a couple of months back and was pretty much an expert there. So I want to know as much as possible about Ubuntu as well. Please don't mind. :)

---

### Post by john newbuntu on 2010-01-16
Keep your system up to date using update-manager(esp ureadahead).

See what you have in /etc/udev/rules.d/z80_user.rules.  Did you set up any udev rules in this file. If not, just move it out of the way (done remove, but copy it some place else).  Reboot and see it it goes away.

Also check and see if you are able to read from USB flash drives?

---

### Post by nishant.singh28 on 2010-01-17
> **john newbuntu said:**
> Keep your system up to date using update-manager(esp ureadahead).

See what you have in /etc/udev/rules.d/z80_user.rules.  Did you set up any udev rules in this file. If not, just move it out of the way (done remove, but copy it some place else).  Reboot and see it it goes away.

Also check and see if you are able to read from USB flash drives?
Everything is up to date. I update regularly.
Got rid of the first message.
As far as reading from flash drives is concerned, if you mean to say can I read and write data then yes, definitely. I have a portable drive of 250 GB permanently connected on 1 port. I hava a notebook cooler and a keyboard connected to the 2nd port. The third port is free. I have connected all sorts of things ranging from my Camera to my ipod to my phone to my flash drive and everything works like a charm. No problems whatsoever.

---

### Post by nishant.singh28 on 2010-01-17
```
nishant@Nishant-Studio:~$ lsusb
Bus 003 Device 005: ID 413c:8156 Dell Computer Corp. 
Bus 003 Device 004: ID 413c:8158 Dell Computer Corp. 
Bus 003 Device 003: ID 413c:8157 Dell Computer Corp. 
Bus 003 Device 002: ID 0a5c:4500 Broadcom Corp. 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 0603:00f2 Novatek Microelectronics Corp. 
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bc2:2300 Seagate RSS LLC 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:63eb Microdia 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
nishant@Nishant-Studio:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:01.0 PCI bridge: Intel Corporation Mobile 4 Series Chipset PCI Express Graphics Port (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M92 [Mobility Radeon HD 4500 Series]
01:00.1 Audio device: ATI Technologies Inc R700 Audio Device [Radeon HD 4000 Series]
04:00.0 Network controller: Intel Corporation Wireless WiFi Link 5100
08:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5784M Gigabit Ethernet PCIe (rev 10)
09:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
09:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
09:01.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
09:01.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
```

---

### Post by nishant.singh28 on 2010-01-17
OK people, I had a conversation with john and he suggested that I interchange the USB devices during boot and see if that makes any difference. The answer, unfortunately, is no. No difference whatsoever.

---

### Post by nishant.singh28 on 2010-01-17
Bump!!!

---

### Post by nishant.singh28 on 2010-01-18
Bump!!!

---

### Post by nishant.singh28 on 2010-01-19
Bump!!

---

### Post by nishant.singh28 on 2010-01-21
Come on people!!! Anyone!!!!

---

### Post by nishant.singh28 on 2010-01-21
Another bump!!!

---

