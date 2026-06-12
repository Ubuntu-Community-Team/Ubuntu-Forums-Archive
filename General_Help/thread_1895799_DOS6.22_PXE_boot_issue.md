---
title: "DOS6.22 PXE boot issue"
date: 2011-12-15
forum: General Help
---

### Post by ctbfalcon on 2011-12-15
So I have a need to boot to ms dos to run ghost in order to ghostcast image a number of pcs.

I have a working ubuntu PXE server that can boot from a variety of sources.
Ubuntu live CD
Linux System Rescue CD
Bart Iso
Dell Diag iso
And a plain unmodified .img file of a dos 6.22 disk.
All boot correctly.

Now I also have a USB drive that boots to msdos and also has ghost and other things to enable TCP/IP.  Which works just fine booting on its own.

but I dont want to have 100s of usb drives sitting around.  I want to PXE boot the same contents of the working dos bootable usb drive with PXE.


i've tried to dd the sub drive to an iso but it does not boot. says: "non-system disk or disk error"

if i try to open the newly made iso with ubuntu archive manager it says its not in ISO 9660 format.

I need more space than the img file will let me have.  I tried to edit the working dos622 img file to add to it what i need but it only hold 1.44mb of data.

So now i am stuck trying to get a working usb dos boot drive to pxe boot from ubuntu.

Any help?

---

### Post by ctbfalcon on 2011-12-15
So i found this:

[http://www.allbootdisks.com/downloads/ISO/AllBootDisks_ISO_Image_Downloads25/DOS6.22_bootdisk.iso](http://www.allbootdisks.com/downloads/ISO/AllBootDisks_ISO_Image_Downloads25/DOS6.22_bootdisk.iso)

i put that into my pxe server with this menu item
label Dos Boot
lernel memdisk
append iso raw initrd/=DOS6.22_bootdisk.iso

This kinda boots.  it drops to a prompt talking about missing command.com

so that is pretty close.  assuming it worked all i would have to do is edit the iso, add my files/customization's and it would work.

Why am i getting that error about command.com

---

