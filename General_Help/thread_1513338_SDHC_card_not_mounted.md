---
title: "SDHC card not mounted"
date: 2010-06-19
forum: General Help
---

### Post by rap3point0 on 2010-06-19
I am using UNE 10.04 and when I place my SDHC card in my netbook's built in sd card reader it doesn't do anything and shows no signs of the cards existence.  I am dual booting with windows 7 which does recognize the card.

Thanks.

---

### Post by davidmohammed on 2010-06-19
it could be that lucid does not genuinely not read sdhc cards on your PC - or it could be that it doesnt see you sd card reader.

If you insert a standard SD card - can it see the card?

If not, please dump the contents (between code tags) for the following run in a terminal session

lsusb

and

lspci

---

### Post by rap3point0 on 2010-06-19
Sorry I am new to ubuntu (and linux in general) so I don't fully get what you mean by dump the content, but the results were
  	 	 	 	 	 	  

Lsusb results
 

 Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub 
 Bus 001 Device 007: ID 0cf2:6250 ENE Technology, Inc.  
 Bus 001 Device 002: ID 064e:a102 Suyin Corp.  
 Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub 
 

 lspci results
 00:00.0 Host bridge: Intel Corporation N10 Family DMI Bridge 
 00:02.0 VGA compatible controller: Intel Corporation N10 Family Integrated Graphics Controller 
 00:02.1 Display controller: Intel Corporation N10 Family Integrated Graphics Controller 
 00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02) 
 00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) 
 00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) 
 00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02) 
 00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) 
 00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) 
 00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) 
 00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) 
 00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) 
 00:1f.0 ISA bridge: Intel Corporation NM10 Family LPC Controller (rev 02) 
 00:1f.2 SATA controller: Intel Corporation N10/ICH7 Family SATA AHCI Controller (rev 02) 
 00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02) 
 01:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0) 
 02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01) 









sorry for my lack of knowing what you mean

---

### Post by davidmohammed on 2010-06-19
is this an Acer Aspire One?

If so, several people have reported the same issue.

Don't know if there is a fix yet

---

### Post by rap3point0 on 2010-06-19
I am using a gateway lt2119u one of their netbooks.
Thanks for the information

---

### Post by davidmohammed on 2010-06-19
...

  its worth reading [this page]("https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Acer Aspire One - Model ZA7 (manufactured 2009)") and searching for your model.  It mentions acer aspire and card reader issues - some have workarounds, some dont.

---

### Post by davidmohammed on 2010-06-19
... ok cross post.

It looks like your netbook shares the same card reader as the acer.  Therefore it will suffer from the same issues.  Still work looking at that page for both your laptop model and for acer models.  Possibly there is a workaround that may work for you.

---

### Post by MooPi on 2010-06-19
Can you insert an SD card and type:
```
sudo fdisk -l
```Post contents back here. That is dash L as in Larry
Also do you have an led indicator light that shows activity on the card reader. If so check to see if it lights up.
There is a small possibility that the machine can see the card but isn't mounting.

---

### Post by rap3point0 on 2010-06-19
Thanks again for all your help.

---

### Post by avacado on 2010-10-14
I have updated the linux netbook compatibility page to reflect that the acer aspire one D260 card reader does not YET have a driver, see
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/633852)
other distributions have the same issue- no driver

It may take some time for a volunteer developer to write the driver.
In the mesn time may I suggest using an external card reader or camera as an external drive.

please subscribe to my bug so you add weight to the issue

---

### Post by phpmonkey on 2011-02-21
Thanks, avacado. There is now a fix in a [duplicate bug report]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277")'s comments: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277/comments/138](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/530277/comments/138)

I too have an Aspire One D260 and it worked for me :popcorn:

---

