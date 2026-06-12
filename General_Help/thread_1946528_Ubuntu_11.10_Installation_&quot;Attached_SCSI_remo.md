---
title: "Ubuntu 11.10 Installation: &quot;Attached SCSI removable disk&quot; HANG"
date: 2012-03-25
forum: General Help
---

### Post by FrankQC on 2012-03-25
I've tried installing Ubuntu 11.10 as well as Fedora 16. I have uploaded a picture of the error, which happens prior to the installation process (regardless of selecting to install 'nor trying Ubuntu without installing).

Has anyone ever had this problem before?

Any help is much appreciated.

---

### Post by dcstar on 2012-03-25
> **FrankQC said:**
> I've tried installing Ubuntu 11.10 as well as Fedora 16. I have uploaded a picture of the error, which happens prior to the installation process (regardless of selecting to install 'nor trying Ubuntu without installing).

Has anyone ever had this problem before?

Any help is much appreciated.

Unplug the USB drive and then boot the install CD.

---

### Post by FrankQC on 2012-03-25
> **dcstar said:**
> Unplug the USB drive and then boot the install CD.

I would, but unfortunately I have no CD/DVD ROM. I am stuck using USB to install Linux. Worked perfectly fine with Windows 7 install via USB.

---

### Post by Subidubi32 on 2012-03-25
I have installed an Ubuntu from a pendrive, but there wasn't any error. [http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/](http://www.pendrivelinux.com/create-a-ubuntu-9-10-live-usb-in-windows/)

---

### Post by Subidubi32 on 2012-03-25
Have you tried this Universal USB-installer?

---

### Post by FrankQC on 2012-03-25
> **Subidubi32 said:**
> Have you tried this Universal USB-installer?

Thank you for the response. However, this did not work as I continued getting the same error in the original post :(

---

### Post by bonfire89 on 2012-03-26
that is the last error message you got? You have an SSD, it shouldn't matter, but it would be interesting to see what would happen if you booted without the SSD attached.

If it is because of the fact that you are booting off USB, and don't have a CD rom drive, there are a bunch of other methods of installing as seen here [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) they aren't quite as easy, but they could be a fun experiment.

you could also try the alternative installer iso found here [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download) particularly if you think the issue might be related to your graphics card.

Also, what filesystem is the thumb drive? I assume it wouldn't like ntfs

There is also an interesting comment here

[http://askubuntu.com/questions/106743/ssd-not-found-during-installation](http://askubuntu.com/questions/106743/ssd-not-found-during-installation)

> Apparently the problem had something to do with the hardware of my motherboard, it uses a marvell adapter for an addition 3 sata ports. The devices that were plugged into these ports weren't found by ubuntu, once i plugged them into the normal sata ports provided on my motherboard the devices were found.

---

### Post by FrankQC on 2012-03-27
> **bonfire89 said:**
> that is the last error message you got? You have an SSD, it shouldn't matter, but it would be interesting to see what would happen if you booted without the SSD attached.

If it is because of the fact that you are booting off USB, and don't have a CD rom drive, there are a bunch of other methods of installing as seen here [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation) they aren't quite as easy, but they could be a fun experiment.

you could also try the alternative installer iso found here [http://www.ubuntu.com/download/ubuntu/alternative-download](http://www.ubuntu.com/download/ubuntu/alternative-download) particularly if you think the issue might be related to your graphics card.

Also, what filesystem is the thumb drive? I assume it wouldn't like ntfs

There is also an interesting comment here

[http://askubuntu.com/questions/106743/ssd-not-found-during-installation](http://askubuntu.com/questions/106743/ssd-not-found-during-installation)

I decided to go ahead and unplug my SSD and boot. The error persists. The thumbdrive is FAT32 and not NTFS. 

My graphics card is an EVGA GTX 570.

This problem is really weird.

---

### Post by piccirilli on 2012-03-28
I am having the same problem. I just build a new computer and am trying to install Ubuntu when installation stalled at "attached SCSI removable disk." Sadly Windows installed just fine. 

Please tell me if you figured this one out.

---

### Post by piccirilli on 2012-03-29
I tried booting from a live CD as suggested by one of the earlier replies. I saw no difference - still the same - installation stalls at "attached SCSI removable disk.

---

### Post by FrankQC on 2012-03-29
> **piccirilli said:**
> I tried booting from a live CD as suggested by one of the earlier replies. I saw no difference - still the same - installation stalls at "attached SCSI removable disk.

Could you please list your computer's hardware? Maybe we can narrow down which hardware could be causing this.

Below is my list:

CPU: Intel Core i7 2700K
MOBO: EVGA Z68 SLI ATX Z68
SSD: Mushkin Chronos 120GB 2.5IN SATA3 Sandforce SF-2281
RAM: Mushkin Enhanced Silverline Stiletto 16GB 4x4GB PC3-10666 DDR3-1333 9-9-9-24
PSU: Corsair Enthusiast Series TX750M 750W ATX Modular
GPU: EVGA GeForce GTX 570 Fermi 732MHZ 1280MB GDDR5
CASE: Silverstone Temjin TJ09B-W Black E-ATX

---

### Post by piccirilli on 2012-03-29
Intel Core i7-960 Bloomfield 3.2GHz
OCZ Agility 3 120GB SATA III SSD
G.SKILL Ripjaws Series 12GB (3 x 4GB) SDRAM
ASUS Sabertooth X58 LGA 1366 Motherboard

---

### Post by FrankQC on 2012-03-29
> **piccirilli said:**
> Intel Core i7-960 Bloomfield 3.2GHz
OCZ Agility 3 120GB SATA III SSD
G.SKILL Ripjaws Series 12GB (3 x 4GB) SDRAM
ASUS Sabertooth X58 LGA 1366 Motherboard

Interesting. I tried without SSD and it still has the error as well. We have different everything else.

I'm starting to think it's an error after the attached SCSI, but it doesn't show. Not sure. Would be nice if more people had this problem to increase the chances of solutions

---

### Post by piccirilli on 2012-03-29
I am contacting the Canonical tech support for help. I'll let you know what they say.

---

### Post by piccirilli on 2012-03-29
Couple updates:

I disconnected my ssd and tried booting from either usb or live-cd. In the case of usb, I received the same message: "attached SCSI removable disk." In the case of live-cd, I got : "firewire_core: created device tf0: GUID ... ." There are some threads on the second message elsewhere - maybe it can be a clue. 

On the positive note: I didn't encounter any problems booting LPS-1.3.1_public_delux from a USB. So, I am going to try to run either CentOS or OpenSuse.

---

### Post by FrankQC on 2012-03-29
> **piccirilli said:**
> Couple updates:

I disconnected my ssd and tried booting from either usb or live-cd. In the case of usb, I received the same message: "attached SCSI removable disk." In the case of live-cd, I got : "firewire_core: created device tf0: GUID ... ." There are some threads on the second message elsewhere - maybe it can be a clue. 

On the positive note: I didn't encounter any problems booting LPS-1.3.1_public_delux from a USB. So, I am going to try to run either CentOS or OpenSuse.

It's a shame that I can't use Ubuntu but another distro. I shall try other distros.

They could not come up with a fix to the problem?

---

### Post by piccirilli on 2012-03-29
The tech support will get back to me within 2 business days. I'll post if they have some good suggestions to try out.

---

### Post by dcstar on 2012-03-30
> **piccirilli said:**
> The tech support will get back to me within 2 business days. I'll post if they have some good suggestions to try out.

Trying the 12.04 Beta is always an option.

---

### Post by piccirilli on 2012-03-30
Problem solved.

Per the David's recommendation I downloaded 12.04 beta (precise-alternate-i386.iso -  Alternate install CD for PC (Intel x86) computers (standard download)) from [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

The trick is that I had to boot from a CD. USB boot kept asking to load from the CD-ROM drive.

---

### Post by FrankQC on 2012-03-30
> **piccirilli said:**
> Problem solved.

Per the David's recommendation I downloaded 12.04 beta (precise-alternate-i386.iso -  Alternate install CD for PC (Intel x86) computers (standard download)) from [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

The trick is that I had to boot from a CD. USB boot kept asking to load from the CD-ROM drive.

Awesome. I'm gonna try to boot it from USB. I'll let you know what happens on my system!

---

### Post by FrankQC on 2012-03-30
> **piccirilli said:**
> Problem solved.

Per the David's recommendation I downloaded 12.04 beta (precise-alternate-i386.iso -  Alternate install CD for PC (Intel x86) computers (standard download)) from [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

The trick is that I had to boot from a CD. USB boot kept asking to load from the CD-ROM drive.

p.s. why not download 64 bit? You have 12 gigs of memory.

---

### Post by FrankQC on 2012-04-01
Update: Tried running 12.04. It reaches the main menu and loops (I click on 'install' and it goes back to main menu).

Outcome is attached.

---

### Post by bonfire89 on 2012-04-01
have you tried the alternative cd yet?

---

### Post by FrankQC on 2012-04-01
> **bonfire89 said:**
> have you tried the alternative cd yet?

I did, yes. It was the precise alternate iso of Ubuntu 12.04, 64 bit.

---

### Post by dcstar on 2012-04-02
> **FrankQC said:**
> Update: Tried running 12.04. It reaches the main menu and loops (I click on 'install' and it goes back to main menu).

Outcome is attached.

That is a Windows load error, it has **nothing** to do with Ubuntu.

---

### Post by FrankQC on 2012-04-02
> **dcstar said:**
> That is a Windows load error, it has **nothing** to do with Ubuntu.

I know it has nothing to do with Ubuntu, unless Ubuntu is the reason this error happened (which it is).

If Ubuntu is the reason this happened then maybe it would be good for the developers to look into it, as there is potential of screwing up the mbr before even installing Ubuntu.

Regardless of this error, Ubuntu 12.04 doesn't start the install process on the system.

---

