---
title: "Advice on Grub 2"
date: 2011-06-20
forum: General Help
---

### Post by Quarkrad on 2011-06-20
I have just rebuilt a 10.10 machine (new motherboard) dual booting with winxp.  7 out of 10 times I boot OK but 3 out of 10 I get a blank screen that just says GRUB with a blinking cursor top left of screen.  The only way to boot to the normal grub screen (with OS options) is to switch off and then on.  My ext 4 partition is on sda 1 and my boot partition (which has winxp on it) is sda 2.  What can I do/check to make grub more robust?  (Not sure why during the install the boot partition was assigned to sda2).

---

### Post by pqwoerituytrueiwoq on 2011-06-20
check master/slave settings on the hard drives there is a jumper that does this
if you need to look up cable select
[IMG]http://www.doublehammer.com/clinic/images/jumpers.jpg[/IMG]

---

### Post by Quarkrad on 2011-06-20
I have bit of a complicated set up - not sure if it right.  I have two HD's in my machine.  The drive with Ubuntu/winXP on it is an IDE drive jumpered as a Master drive.  It has a a SATA adapter plugged into it and connected to the motherboard via a SATA (sata 1) socket.  My 2nd HD is just used for storage/back up and is a SATA drive connected to the motherboard via a SATA socket (sata 2).  This set was OK prior to the latest rebuild - nothing has really changed.

---

### Post by pqwoerituytrueiwoq on 2011-06-20
assuming /boot is on the sata drive set the ide to slave and if possible set the sata drive to master

---

### Post by vhradice on 2011-06-20
SATA Drives do not have master/slave setting.  Where it is plugged into the mb determines its address.  At boot time, look at the boot up messages to see what is being called Sata1, Sata2.  The drive that you want to boot from should be Sata1.  Also check boot order in BIOS settings to make sure you are booting from the correct drive.  It sounds like sometimes if you reboot without powering off, the bios gets confused as to which drive to boot from.  Hope this helps.

---

### Post by Quarkrad on 2011-06-21
I will try that and see how it goes. My bios (Foxconn) is a little strange in that I have a boot sequence list and a hard disk list which also seems to have a relationship to the boot order according to the documentation. I have made sure the correct drive is the first in the boot sequence and deleted the 2nd drive from the hard drive list.  So far the pc booting ok but not enough times to see if Grub gets confused.  I will monitor -thanks.

---

### Post by Quarkrad on 2011-06-22
It's still not working.  Sometimes I get the message - **Select Proper Boot device** - other times something like **Insert boot media in selected boot device**  or even  [B]Grub loading error: out of disk.  entering rescue mode...

Grub rescue>[/B]

Other times I boot normally into grub. There is something somewhere that is not right.

---

