---
title: "How Does the Size of USB Drive Affect Ubuntu?"
date: 2012-09-11
forum: General Help
---

### Post by daTomoT on 2012-09-11
Hi all. I'm just wondering how creating a pendrive from a 2GB USB stick will differ my experience of a 32GB pendrive? Is it just like having a bigger hardive and new storage space, or will it make it run easier/smoother aswell?

Just another Q attached to this, to save making two threads: How to install microsoft office 2010 set from disk onto Ubuntu 12.04?

~daT.

---

### Post by afulldeck on 2012-09-11
Is it just like having a bigger hardive and new storage space, or will it make it run easier/smoother aswell?
 
Well having a bigger pen drive is having a bigger hardrive. However the speed will depend on throughput which is different depending on whether you are using a USB 2.0 or USB 3.0 drive.  Take a look at this link and explanation. 
 
[http://www.tomshardware.com/reviews/usb-hard-drive,2015.html](http://www.tomshardware.com/reviews/usb-hard-drive,2015.html)
 
In answering your second question, you can follow the instruction here....
 
[https://seogadget.co.uk/how-to-install-virtualbox/](https://seogadget.co.uk/how-to-install-virtualbox/)
 
or you can use Playonlinux 
 
[http://www.youtube.com/watch?v=bh26YBy812M](http://www.youtube.com/watch?v=bh26YBy812M)

---

### Post by newb85 on 2012-09-11
You're asking about running Ubuntu from a USB drive?  I think Ubuntu requires a little more space than 2GB...

---

### Post by daTomoT on 2012-09-12
Thanks for the answers, links are awesome. 

And not meaning I offend, but my 2GB drive which wa the biggest I could find, is running Ubuntu 12.04 for me. 

~daT.

---

### Post by 2F4U on 2012-09-12
If you create the usb stick in persistent mode, you can store documents and settings on the usb stick (different from a cd, on which you can't store anything). So, bigger usb drives allow you to store more individual data on it.

[http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu](http://www.ubuntu.com/download/help/create-a-usb-stick-on-ubuntu)

---

### Post by newb85 on 2012-09-12
> **daTomoT said:**
> Thanks for the answers, links are awesome. 

And not meaning I offend, but my 2GB drive which wa the biggest I could find, is running Ubuntu 12.04 for me. 

~daT.

Are you certain it's a 2GB drive, and not a 2TB drive?

---

### Post by Wim Sturkenboom on 2012-09-12
> 
Are you certain it's a 2GB drive, and not a 2TB drive?

I like a 2TB USB memory stick; please ship me one :D

Ubuntu liveCD fits on 2GB; source: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
I guess it will leave about 1GB for persistence.

---

### Post by mcduck on 2012-09-12
> **newb85 said:**
> You're asking about running Ubuntu from a USB drive?  I think Ubuntu requires a little more space than 2GB...

2GB is easily enough for a live USB. Even 1GB drive would work, you only need the same amount of space the Ubuntu disc image takes. A normal install would of course require more space.

Anyway, what comes to the size of the drive, keep in mind that the nomral way of creating live setup with persistence only allows up to 4GB of space for the persistence file because the install uses FAT filesystem, which has 4GB limit on file size. You *can* work around that by creating a separate Ext partition on the USB drive and using that for the persistence, but you'll have to do that manually...

---

### Post by newb85 on 2012-09-12
> **Wim Sturkenboom said:**
> I like a 2TB USB memory stick; please ship me one :D

Ubuntu liveCD fits on 2GB; source: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
I guess it will leave about 1GB for persistence.

Point taken.

I was thinking "drive", not "stick", and mistakenly thought the OP was installing Ubuntu on it, rather than simply setting it up as a persistent LiveCD.  Obviously, if it has more space than a CD, it can be used as a LiveCD.

---

