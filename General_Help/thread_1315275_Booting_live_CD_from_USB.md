---
title: "Booting live CD from USB"
date: 2009-11-05
forum: General Help
---

### Post by Magican on 2009-11-05
Hi @ all,
 
I have a problem with booting ubuntu from USB.
I used an ISO of Ubuntu 8.10 "Intrepid Ibex" - Release i386
The Bootloader is Grub4Dos.
I can boot till the following sequenz
[8.974657] sr 6:0:0:1: Attached scsi generic sg3 type 5.
If I wait two minutes the BusyBox started.
can anybody help me in this case?
Thank you in advance

---

### Post by phillw on 2009-11-05
> **Magican said:**
> Hi @ all,
 
I have a problem with booting ubuntu from USB.
I used an ISO of Ubuntu 8.10 "Intrepid Ibex" - Release i386
The Bootloader is Grub4Dos.
I can boot till the following sequenz
[8.974657] sr 6:0:0:1: Attached scsi generic sg3 type 5.
If I wait two minutes the BusyBox started.
can anybody help me in this case?
Thank you in advance


Hi, I send people over this way, for all things usb --->> [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

There is also [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)  highly recommended by some - I just happen to use the pendrive site & can report back that it works.

Phill.

---

### Post by Magican on 2009-11-05
> **phillw said:**
> Hi, I send people over this way, for all things usb --->> [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
 
There is also [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/) highly recommended by some - I just happen to use the pendrive site & can report back that it works.
 
Phill.
 
Hi Phil,
Thank you for your statement but that is not what i am looking for.
I have created a Multibootstick. 
With a Boot Menu and I am looking for a stable live system, preferd ubuntu, which is NOT persistent. So that you nerver can change anything.
 
regards

---

### Post by P4man on 2009-11-05
> **Magican said:**
> Hi @ all,
 
I have a problem with booting ubuntu from USB.
I used an ISO of Ubuntu 8.10 "Intrepid Ibex" - Release i386
The Bootloader is Grub4Dos.
I can boot till the following sequenz
[8.974657] sr 6:0:0:1: Attached scsi generic sg3 type 5.
If I wait two minutes the BusyBox started.
can anybody help me in this case?
Thank you in advance

Are you getting the live cd main menu before you see that error? The menu where you can select keyboard layout and chose memory test and all that?

If you cant, see above post.

If you can, then try disabling your cdrom drive in your bios. Od disable AHCI if you have that option (somewhere in ide settings)

---

### Post by Magican on 2009-11-05
> **P4man said:**
> Are you getting the live cd main menu before you see that error? The menu where you can select keyboard layout and chose memory test and all that?
 
If you cant, see above post.
 
If you can, then try disabling your cdrom drive in your bios. Od disable AHCI if you have that option (somewhere in ide settings)
 
Hi P4man,
 
I can see the boot menu and pressed f6 and deleted "Queit" and "spalsh" in boot options to geht these information.
I tryed to disabeld cdrom and AHCI. 
I have posted the last lines which I get in BusyBox with "dmesg  | tail"

---

### Post by P4man on 2009-11-05
hmm.. have you tested the usb stick on a different machine? Or alternatively, have you tried another stick?

---

### Post by Magican on 2009-11-06
Yes, I have tested it several times.
I tested one hour ago the latest version, there I get the following:
/sr1 not found 
no bootable medium found.
The stick can boot Knoppix without any error or warning.

---

### Post by Magican on 2009-11-09
has nobody any idea?

---

### Post by P4man on 2009-11-09
did you test the stick on a different machine? The perhaps the ISO is damaged, try downloading it again (preferably using bittorrent) ?

---

### Post by phillw on 2009-11-09
> **Magican said:**
> has nobody any idea?

As mentioned, check the iso that you have saved.  [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)   has info on doing so.

Phill.

---

