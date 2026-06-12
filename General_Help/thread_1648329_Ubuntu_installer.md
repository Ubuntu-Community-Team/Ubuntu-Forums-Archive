---
title: "Ubuntu installer?"
date: 2010-12-18
forum: General Help
---

### Post by BlackLab on 2010-12-18
Hi all,
I want to dual boot my netbook with xp and ubuntu. I don't have a 2Gig pen drive to install Ubuntu onto in order to then install it onto the netbook's hdd.

However I am currently using Ubuntu, installed on an external hdd connected to my netbook.
Is there an installer I can download onto this Ubuntu which can then [be] use to set up the dual boot on the netbook's hdd?

cheers.

---

### Post by wilee-nilee on 2010-12-18
How did you install it to the external? You also only need a 1 gig thumb for a install.

---

### Post by BlackLab on 2010-12-18
> **wilee-nilee said:**
> How did you install it to the external? You also only need a 1 gig thumb for a install.

I installed it using a cd on a different laptop .. one that has a cd drive  ... The biggest thumb drive I have is only 256MB .. I did have a 1 Gig one but the damn dog ran off with it and hid it somewhere in the garden .. we've never seen it since.

I think all the installer needs to do is create a partition on the netbook's hdd (shrinking xp), copy over this Ubuntu's image and set up the boot record so that I have the choice of OS on boot. .. seems like it should be possible with some clever command lines in a console ... but .....

---

### Post by wilee-nilee on 2010-12-18
> **BlackLab said:**
> I installed it using a cd on a different laptop .. one that has a cd drive  ... The biggest thumb drive I have is only 256MB .. I did have a 1 Gig one but the damn dog ran off with it and hid it somewhere in the garden .. we've never seen it since.

I think all the installer needs to do is create a partition on the netbook's hdd (shrinking xp), copy over this Ubuntu's image and set up the boot record so that I have the choice of OS on boot. .. seems like it should be possible with some clever command lines in a console ... but .....

Just do a wubi install until you get a cd reader or a thumb your asking for trouble in the way your trying to do it.

---

### Post by 3rdalbum on 2010-12-18
On the computer with the CD drive, install "Unetbootin" and use it to copy the Ubuntu CD/USB image to the external hard disk. Connect the disk to your netbook and boot up from it and install Ubuntu.

When the websites say you can use a USB disk to install Ubuntu, they don't just mean flash drives.

---

### Post by wilee-nilee on 2010-12-18
> **3rdalbum said:**
> On the computer with the CD drive, install "Unetbootin" and use it to copy the Ubuntu CD/USB image to the external hard disk. Connect the disk to your netbook and boot up from it and install Ubuntu.

When the websites say you can use a USB disk to install Ubuntu, they don't just mean flash drives.

So what happens if they need that internal hd install fixed by using a live cd from a thumb or a cd, or a repair to the windows portion.

You give no help on trying to reset the external HD back to running Ubuntu or how to protect it when you use unetbootin, was this the best advice really.;)

Look a 1 gig thumb is like 5$ US having the right tools are important, especially if something needs fixed.

---

### Post by BlackLab on 2010-12-18
> **wilee-nilee said:**
> Just do a wubi install until you get a cd reader or a thumb your asking for trouble in the way your trying to do it.

You've just reminded me .. I do have a USB CD drive somewhere .. I can use that .. thankyou!

---

### Post by BlackLab on 2010-12-18
> **BlackLab said:**
> You've just reminded me .. I do have a USB CD drive somewhere .. I can use that .. thankyou!

ah well, unfortunately the USB CD drive seemed unable to read the Ubuntu CD ..  or something like that .. it's a 'Pika One - RIP Case'

It was recognised in the BIOS and it was all set to boot from it, but for some reason it ignored the CD drive and booted straight to Windows ... I tried a number of times but it just would not work ...

back to the drawing board :(

---

### Post by BlackLab on 2010-12-18
> **BlackLab said:**
> ah well, unfortunately the USB CD drive seemed unable to read the Ubuntu CD ..  or something like that .. it's a 'Pika One - RIP Case'

....................................................... :(

 ... but it's no wonder ... My Ubuntu CD was actually a Ubuntu DVD . and the Pikaone ripcase only reads and writes CDs ..

Currently I am downloading the Ubuntu ISO ..
will try again with a Ubuntu CD

---

