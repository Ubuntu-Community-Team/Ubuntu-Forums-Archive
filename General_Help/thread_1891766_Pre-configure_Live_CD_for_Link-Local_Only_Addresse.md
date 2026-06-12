---
title: "Pre-configure Live CD for Link-Local Only Addresses"
date: 2011-12-06
forum: General Help
---

### Post by tom.davidson58 on 2011-12-06
This is my first post, so if it is a repeat, please forgive me but I have searched the forums and cannot find an answer anywhere else.

The issue I'm having seems simple:
In my line of work, I frequently perform data transfers for customers.  Often times, we are unable to perform these transfers because of a corrupt OS or some weird ethernet driver issue which prevents the machines from communicating with each other.  Normally, I would work around this issue by simply sledding the hard drive, but for legal reasons (i.e. - lack of hardware certification), my company will not allow us to pull drives.  They have, however, agreed to let me use a Linux Live CD as a means of working around these issues to perform the transfer.

The problem comes when we are transferring to Mac computers.  It seems that Linux's implementation of DHCP does not like to assign Link Local Addresses (169.254.x.x) when connected directly to a Mac via ethernet.  I would ask them to provide a router, but waiting for them to actually get it could take ages.  If I go into the "Edit Network Connections" dialog in Gnome, under "IPv4 Settings", I can configure "auto eth0" to assign link local addresses only, but this needs to be done every time we use the CD.

So, to make a long story short - does anybody kow how I can pre-configure the live image to assign only link local addresses?  My first thought was to image a flash drive, boot from that and configure the ethernet port, then make an image of the flash drive and burn that to a CD, but if I image the flash drive with a live CD image, will the flash drive then have a read-only filesystem?

Any help on this matter would be greatly appreciated.

---

### Post by phidia on 2011-12-06
A properly copied disk image/iso to flash drive is also able to be modified so it is not read only-see [this guide]("https://help.ubuntu.com/community/Installation/FromUSBStick"). And the pertinent sentence is this one: > Also, you can configure Ubuntu on the USB flash drive to save changes you make, unlike a read-only CD-ROM drive. 

---

### Post by tom.davidson58 on 2011-12-09
Works like a charm...  only problem is the image is too large for a CD (which I had hoped to use because we do still see some old machines that don't have DVD drives).  Can anyone recommend a tool that I can use to "trim the fat" from the image (i.e. - OpenOffice, the installer tool, Firefox, etc...)?

---

### Post by tom.davidson58 on 2011-12-18
Nobody has a suggestion?

---

