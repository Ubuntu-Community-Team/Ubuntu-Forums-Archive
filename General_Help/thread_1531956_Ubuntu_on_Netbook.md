---
title: "Ubuntu on Netbook"
date: 2010-07-15
forum: General Help
---

### Post by Toshiba_Netbook on 2010-07-15
[INDENT] 							I have a Toshiba NB305 in which the hard drive crashed, it won't  boot up.  That is still an issue, but I've overcome it by downloading  Ubuntu O/S on a USB drive and boot up that way now.  I'm cool with using  Ubuntu, but it doesn't seem to save my settings after each shut  down-startup cycle.  My Evolution settings are gone and all my  add-ons/themes for Firefox need to be reinstalled, etc.  What up with  that? 						[/INDENT]

---

### Post by x C0MMAND0 x on 2010-07-15
If you are just loading the OS off of the USB drive each time, then nothing is saving to your hard drive and you haven't even installed Ubuntu at this point.  Depending on what you have on your hard drive and if you want to back up all of the data first, you could install the Ubuntu OS to your computer's hard drive and then load from that instead of USB every time.  Performance would be GREATLY enhanced by this method also.

Ubuntu isn't really designed to run from a USB as a main OS, the purpose of the Ubuntu .img is to try/test Ubuntu or to install it on Netbooks which don't have CD drives.

Lastly, check out [Ubuntu 10.04 Netbook Edition]("http://www.ubuntu.com/netbook/get-ubuntu/download") which might suit your performance needs better.

Edit:  If you have multiple USB drives on your netbook you can boot to Ubuntu via 1 USB drive, and then copy all of your Windows data that you need (files/music/whatever) to another USB drive as a backup, that way you can install Ubuntu and get rid of Windows and then copy your data back over.  Be sure you have everything backed up and you understand what overwriting everything means before you do it, especially if you are new to Linux/Ubuntu.  If you have any questions just ask

---

### Post by Toshiba_Netbook on 2010-07-19
Thanks for the help, I'm trying to install Ubuntu on the hard drive, but it appears I may have a bigger issue on hand.

1st issue: when the partitioning step appears, it says this computer has no hard drive installed.

2nd issue: The installation continues and gets to 66% complete, when an error box pops up reading the following.
-----
Installation Failed
The installer encountered an error copying files to the hard disk:
[Errno 30] Read-only file system: '/target/boot/vmlinuz-2.6.32-21-generic'
This is often due to a faulty hard disk. It may help to check whether the hard disk is old and in need of replacement, or to move the system to a cooler environment.
-----

I presume this is a bad thing.  What are my options at this point?  TIA

-James

---

### Post by cloyd on 2010-07-19
I am not the ultimate problem solver on these pages, but if I read your first post right, your hard disk crashed. I'd think that you aren't going to be able to install anything on this drive. Have you been accessing this drive for data? If not, I suspect you need a new drive. If you can't buy a new drive, I think that either someone can tell you, or somewhere on the forums you can get instructions to make a persistent usb drive. That is not the best solution in the world, but it would be ok for a while until you could get a new drive. 

In addition, if you don't have a hard drive for data, I'd suggest that you get as big a usb drive as you possibly afford. I'd want at least 16 gig. You really need a hard drive. Even if you are able to make a flash drive persistent and make it work, it will probably have a somewhat short lifespan due to all the constant writing to the drive.

---

### Post by Toshiba_Netbook on 2010-07-20
I was expecting as much.  I can't do the system restore through Toshiba.  I have NO idea how this happened.  Not cool.

Any recommendations for a HD replacement?  Saw [this](http://www.toshibadirect.com/td/b2c/adet.to?poid=450212) on Toshiba's website.  I'm also intrigued by [Momentus XT's 7200 RPM drive](http://www.seagate.com/www/en-us/products/laptops/laptop-hdd) and [Western Digital's Scorpio Blue drives](http://www.wdc.com/en/products/products.asp?driveid=506). I'd probably go around 500GB or 750GB, but am not certain about SATA or solid state.

---

### Post by gordintoronto on 2010-07-20
A USB installation will save settings if it is marked as "persistent." USB Startup Disk Creator has an option to make it persistent.

I made one USB stick persistent by editing /syslinux/syslinux.cfg (*not* the file in the root of the flash drive), adding the word "persistent" in the line which begins "append".

---

