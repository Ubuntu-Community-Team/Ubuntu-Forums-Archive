---
title: "Damaged hard drive :( PLEASE HELP! recovering the data/imaging the drive"
date: 2011-03-16
forum: General Help
---

### Post by markeee on 2011-03-16
hi!

Wasn't really sure where to put this but maybe someone could help me out, if anyone has any idea how to fix / get data off damaged hard drives -- or any links which could help me!!

Im trying to get the data off it, either by slowly copying the files from the damaged drive to a new one, or making an image of the entire drive!!


The other week I turned on my lacie 1tb HDD, and it made weird noises, tick, tick etc - (day before it was working fine)

I've tried it in a windows netbook and it recognises a USB device, but it never becomes accessible

Does anyone have any experience with this, what programs/utilities or anything, any sites which could help? I'd l

I have googled but keep coming across links for recovering a drive after OS failure/partition table corrupt

ANY help is greatly appreciated

thanks

---

### Post by pqwoerituytrueiwoq on 2011-03-16
read through this
[http://ubuntuforums.org/showthread.php?t=1704894](http://ubuntuforums.org/showthread.php?t=1704894)
it may be of use for you

does the disk sound like it spins?

---

### Post by satish_j on 2011-03-17
@pqwoerituytrueiwoq,
I assume the link you provided is of different issue.You were able to login to ubuntu,whereas here,i think the OP is not even able to boot from Harddisk
@markee--does the damaged HardDrive is getting detected in BIOS??If not,then i dont think there is any way to recover the data from it as it has damaged beyond repair..

---

### Post by markeee on 2011-03-17
> **pqwoerituytrueiwoq said:**
> read through this
[http://ubuntuforums.org/showthread.php?t=1704894](http://ubuntuforums.org/showthread.php?t=1704894)
it may be of use for you

does the disk sound like it spins?

not sure, it just makes clicking noises at the moment :(

---

### Post by markeee on 2011-03-17
> **satish_j said:**
> @pqwoerituytrueiwoq,
I assume the link you provided is of different issue.You were able to login to ubuntu,whereas here,i think the OP is not even able to boot from Harddisk
@markee--does the damaged HardDrive is getting detected in BIOS??If not,then i dont think there is any way to recover the data from it as it has damaged beyond repair..

It's not the main drive, it's a 1tb external drive, connected via USB -

It just doesn't seem to get picked up so I can't access it:(

I could try forcing it to mount then using ddrescue on it? Either force a mount with it connected using USB or internally via SATA?

I was reading about trying to use ddrescue to create an img file from the disk, as ddrescue skips parts when it recieves errors/fails and puts them to the end when it keeps trying i think?

Would it be of any benefit to take the drive out of the enclosure and try it inside my desktop? There's a small chance it could be the electronics of the enclosure, although by the fact it makes ticking noises..sounds to me like the HDD itself

I know there's othe rways i.e. head replacement, platter swaps etc but these all cost big bucks !
thanks

---

### Post by mike555 on 2011-03-17
It might not be getting enough power , if it is usb powered try plugging into a powered usb hub ...

---

### Post by pqwoerituytrueiwoq on 2011-03-17
> **satish_j said:**
> @pqwoerituytrueiwoq,
You were able to login to ubuntu
there was nothing to login to (/home was MIA) i was able to do stuff on a live cd

> **pqwoerituytrueiwoq said:**
> does the disk sound like it spins?
unless it is a ssd then it can't

---

### Post by dragonfly41 on 2011-03-17
I would agree with Mike555.   

Use a powered USB hub or plug in directly to your PC to avoid reduced power supply.

I have been trying to interface an external CD-RW device connected through an unpowered USB hub (the device drew power from a USB port) and it would not work properly until today I read about power supply sensitivity and I plugged the device directly into my laptop and not through an unpowered USB expander.   

Then I was able to burn discs.

---

### Post by markeee on 2011-03-17
> **dragonfly41 said:**
> I would agree with Mike555.   

Use a powered USB hub or plug in directly to your PC to avoid reduced power supply.

I have been trying to interface an external CD-RW device connected through an unpowered USB hub (the device drew power from a USB port) and it would not work properly until today I read about power supply sensitivity and I plugged the device directly into my laptop and not through an unpowered USB expander.   

Then I was able to burn discs.

thanks, i will try this
one thing though - if it was a power issue it wouldn't be making clicking sounds would it? :(

---

### Post by rubylaser on 2011-03-17
Yes a power issue could cause clicking if there's not enough power to spin the disk up. If all else fails, you could remove it from the usb enclosure, and connect it via SATA, and use gddrescue to recover what you can.

[https://help.ubuntu.com/community/DataRecovery#Imaging a damaged device, filesystem or drive]("https://help.ubuntu.com/community/DataRecovery#Imaging a damaged device, filesystem or drive")

---

