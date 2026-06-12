---
title: "Can you boot from a flash drive?"
date: 2011-03-25
forum: General Help
---

### Post by tc101 on 2011-03-25
Would it be possible, and would it make sense, to copy the whole utuntu file system to a portable flash drive, and then plug it into another computer and run ubuntu on that computer?

---

### Post by .:PiXi²:. on 2011-03-25
Yes, that would be possible. Run usb-creator-gtk in ubuntu to install a fresh copy of ubuntu onto a flash drive. Copying an existing ubuntu installation onto a flash drive is a bit more difficult, you have to make the flash drive bootable first, using unetbootin.

---

### Post by oldfred on 2011-03-25
It is functional. I have Natty installed to my 16GB flash drive - 8GB for install & 8GB for data. USB is slower than a hard drive & flash is slow especially on writes. Install & updates run slow but system is usable.

As long as your computer lets you boot USB, most newer do, then it is just like any install to a second drive, but you should make some extra settings to reduce writes.

It does not have to be encrypted:
Standard full install to flash or SSD:
Ubuntu Encrypted Flash Memory  Installation
[http://members.iinet.net/~herman546/p19.html]("http://members.iinet.net/%7Eherman546/p19.html")
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)

Use ext2 or ext4 without journal:
tune2fs -O ^has_journal /dev/sda1
No swap or set swapiness
After installing, change the fstab so that everything gets mounted with noatime.
change to noop i/o scheduler

You want journal to speed up system recovery if you have to do repairs or run fsck. But if partition is small then it does not take long to fsck anyway and without journal writing is reduced.

Installing Ubuntu in Hard Disk Two (or more) internal or external
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")

You can also install multiple ISO to one USB. I did it manually before I learned about several users that have created scripts to automate the process.

This is a script to install many ISOs. Some that will not loopmount by installing a kernel and boot image.
MultiBootUSB - Install and boot multiple Linux from Pendrive / Flash drive / USB disk 
[http://ubuntuforums.org/showthread.php?t=1518273](http://ubuntuforums.org/showthread.php?t=1518273)
[http://blog.p-mt.net/archives/644](http://blog.p-mt.net/archives/644)
[http://liveusb.info/dotclear/](http://liveusb.info/dotclear/)

multicd.sh - combine Linux ISOS into one CD
[http://ubuntuforums.org/showthread.php?t=1071869](http://ubuntuforums.org/showthread.php?t=1071869)
[http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/](http://www.pendrivelinux.com/multiboot-create-a-multiboot-usb-from-linux/)

ISO Booting with Grub 2 - drs305
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
HOWTO: Boot & Install Ubuntu ISO from the Grub Rescue Prompt
[http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293)
MultiBoot USB with Grub2 (boot directly from iso files)
Basically you just install grub2, create a folder for the isos and edit a grub.cfg to loop mount the isos.
HOWTO: Booting LiveCD ISOs from USB flash drive with Grub2
[http://ubuntuforums.org/showthread.php?t=1288604](http://ubuntuforums.org/showthread.php?t=1288604)
[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=1535864)

---

### Post by snowpine on 2011-03-25
Yes, of course it is possible... in fact I have an old laptop with a busted hard drive, happily running Linux from an 8gb flash drive. :)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by ppeterb on 2011-03-25
Assuming your system can boot from a usb drive . . . 

For more than 2 years I have been using remastersys to make a .iso file from the running Ubuntu system. Start at [http://www.remastersys.com/](http://www.remastersys.com/) and read about it. I suggest using the -gui unless you like geeky details.

Then I use unetbootin to write the usb thumb drive and install a boot loader. Start at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)  A 4GB drive is fine. I typically use an 8GB or 16GB pqi U339 because they have write protection switches and are very fast.

Both remastersys and unetbootin install in Ubuntu "like real software" although you will need to add the ppa. Nothing unusual.

Caution - unetbootin likes a freshly formatted drive and does not like one otherwise. Suggestion - I've had odd troubles doing a basic format of the drive using Ubuntu specifically and Linux in general. For me -  Win XP's plain old format works just fine.

---

### Post by tpprynn on 2011-03-25
Can I add a question about this which may also have been on the OP's mind? He asks about then running the Ubuntu installation on another computer than the one that did the installing. If you were to do this with XP for example, using an external or moved hard drive at least, any hardware differences would stop the OS from running. Why doesn't this happen with Ubuntu if it doesn't? Thanks.

---

### Post by snowpine on 2011-03-25
> **tpprynn said:**
> Can I add a question about this which may also have been on the OP's mind? He asks about then running the Ubuntu installation on another computer than the one that did the installing. If you were to do this with XP for example, using an external or moved hard drive at least, any hardware differences would stop the OS from running. Why doesn't this happen with Ubuntu if it doesn't? Thanks.

Ubuntu detects hardware at boot.

I assume Microsoft does not allow you to transfer/copy Windows to a different computer because of piracy concerns. No such issue with Ubuntu of course! :)

---

### Post by oldfred on 2011-03-25
The issue Ubuntu may have is, if you install proprietary video drivers and then the other system is different. Either do not install proprietary drivers or make plans how to handle.

Create Portable Ubuntu for 2 different Video Cards - script
[http://ubuntuforums.org/showthread.php?p=8107778](http://ubuntuforums.org/showthread.php?p=8107778)
There is a application named switchconf that lets you choose between xorg.conf files at boot.

---

### Post by Herman on 2011-03-26
:D I agree, for a USB installation that you want to be portable, it's slightly better to avoid installing the additional drivers unless you have a reason for wanting to do so. Ubuntu sets itself up automatically at boot-up well enough for most computers and for the needs of most users.

I like to use Google Earth a lot, and usually I need to install the additional drivers to be able to use google earth properly. Other people might have their own reasons for wanting or needing the specific video card drivers.

If installing drivers for a particular computer results in the USB Ubuntu installation failing to configure the Xserver properly when booting up in some other machine, another very simple fix is to reboot and when  you see your GRUB Boot Menu, use your down-arrow key to go down one line and choose recovery mode instead of the normal Ubuntu bootup.

You can expect to see a lot of scrolling white text and then a blue screen with a gray window in the center called the 'Recovery Menu'.
From the 'Recovery Menu', if you choose 'failsafeX', you will then be offered a list of choices including 'Reconfigure graphics'. That's another way you can reset your Xserver settings and temporarily disable an installed driver. Maybe it's not as neat as having a script like P4man's or a program like switchconf, but I just thought I would mention it in case it appeals to some people or possibly it might be the only thing a person can do in certain circumstances. 

I found the following link about how to use switchconf, _[Changing system configuration: switchconf]("http://meandubuntu.wordpress.com/2008/05/07/changing-system-configuration-switchconf/")_  in case it's any help to others. 
Thanks for your info about P4mans's script and switchconf, oldfred, those look cool and I'm going to give them a try. 

EDIT: So far I have tried out P4man's script, (modified slightly to suit my particular requirements), and it works great, and even works equally well for USBs with Ubuntu in a fully encrypted LUKS LVM file system too. Once set up, it's very convenient for the user, no need to do anything really, the script does everything silently and automatically. I'm impressed.

EDIT: 2011.06.11 - three months later, I'm still using P4man's script for switching my xorg.conf files according to the detected video card at boot time but I am finding that I often have to log in twice. Sometimes the PC will boot up in a decent resolution and sometimes not, logging in and then logging out and back in again seems to fix it. I'm starting to get a little tired of having to do that so often though. I also need to log in and out again an extra time to set up dual monitors in my work PC, and that's adding to the annoyance. I tried moving the P4man's script to /etc/init.d and running update-rc.d nvidia-xconfig defaults 01 02 after reading /etc/init.d/README and  [9.3 System run levels and init.d scripts]("http://www.debian.org/doc/debian-policy/ch-opersys.html#s-sysvinit")  but the problem remains.

Maybe I'll try out switchconf for a while and see if that works better. Developers have already done a great job getting Ubuntu to be able to boot and display the Xserver in just about any PC, but there might still be room for some further improvement here. It would be nice if P4man's script or something like it could be made to work better and be part of Ubuntu so everyone can use it. Alternativley we could benefit from some small extra program that might be able to detect when the same motherboard has been booted previously and use the same hardware settings that the user saved somehow. 

Regards, Herman  :)

---

