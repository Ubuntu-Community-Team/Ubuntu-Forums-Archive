---
title: "Complete use through USB"
date: 2011-03-05
forum: General Help
---

### Post by Newuser9 on 2011-03-05
I want to use my USB as my main hard drive It's a 64Gb one so it has plenty of space for all my Ubuntu needs. Every time I restart so does all my data. Is there any one to get Ubuntu to let me use my USB in this way? 

I apologise if this issue has been brought up before and am grateful for any help that can be offered

Thanks in advance

Pat.

---

### Post by Hedgehog1 on 2011-03-05
Newuser9 (a.k.a. 'Pat'),

Welcome to the forums!

This is possible to do.  I call it **Ubuntu-On-A-Stick!**  The **Real Pocket PC!**.

The easiest way to do it is to open your computer and disconnect your hard drive (be sure it is turned off!).

Then boot the computer with the LiveCD and the USB stick plugged in.  Th CD will see your stick as the hard drive and install.

If you don't want the USB stick to add the Hard Drive partitions to the grub menu on later updates, delete the **/etc/grub.d/30_os-prober** file.

Once the install is done, power off and plug your hard disk back in.  Then you can use the bios to choose to boot from your hard drive, or your **Ubuntu-On-A-Stick!**.

***The Hedge***

:KS

---

### Post by Newuser9 on 2011-03-05
It's already "installed" on the flash drive and I can boot from it(using it now). It just deletes every change I make when I reset, It also has "install ubuntu now" on the desktop. 

I'd also like to, If possible, use it on other pc's so basically I could boot my computer on any pc that supports booting from a Usb. just like a real pocket pc :)

Also it's saying it's only using 2gb or so of the stick.

and what do you mean by "If you don't want the USB stick to add the Hard Drive partitions to the grub menu on later updates, delete the **/etc/grub.d/30_os-prober** file."

---

### Post by Newuser9 on 2011-03-05
Found a great little tutorial... hope it helps anyone else with this problem..

[http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive/)

---

### Post by Hedgehog1 on 2011-03-05
> **Newuser9 said:**
> It's already "installed" on the flash drive and I can boot from it(using it now). It just deletes every change I make when I reset, It also has "install ubuntu now" on the desktop. 

I'd also like to, If possible, use it on other pc's so basically I could boot my computer on any pc that supports booting from a Usb. just like a real pocket pc :)

Also it's saying it's only using 2gb or so of the stick.

and what do you mean by "If you don't want the USB stick to add the Hard Drive partitions to the grub menu on later updates, delete the **/etc/grub.d/30_os-prober** file."

Pat,

What you have on your USB stick is the LiveCD image.  What you WANT is a real install on the USB stick.  To do that, you need to burn a CD, and boot the computer off of that.  Your USB stick will get formatted during the install and become a real Ubuntu install, that saves data and uses all of the USB stick, not just the 2 gigs.  Then you can save music and documents on it.

Lets start with that part, and move on to the 'delete the **/etc/grub.d/30_os-prober** file' part later.

***The Hedge***

:KS

---

### Post by Newuser9 on 2011-03-05
I'm currently doing what the Tutorial I posted told me to do. will I have to worry about Grub loader that way??

---

### Post by Hedgehog1 on 2011-03-05
Pat,

I just follow the tutorial, and what it is installing is different from a complete install.  It is a casper (ghost) drive install.

I don't know if the **/etc/grub.d/30_os-prober** file is even on a casper install.

If you find you are limited to just 4 gigs, you may still have to install from a CD.

Anyway, have fun with the 64gig USB stick - I use a 32gig one and I am running out of space. I wish I had yours!

***The Hedge***

:KS

---

### Post by Newuser9 on 2011-03-05
Where's that file located??

Yeah, but like all things, It came at a price, got a good deal though.

---

### Post by Hedgehog1 on 2011-03-05
Pat,

I updated my post - you have a different install using the tutorial method and may not have that file.

***The Hedge***

---

### Post by Newuser9 on 2011-03-06
Thanks Hedge, You've been a great help!

---

### Post by Hedgehog1 on 2011-03-06
Have fun with it!  It is rather cool, isn't it?

Welcome to the International Society of **Ubuntu-On-A-Stick!** users...

***The Hedge***

:KS

---

### Post by Newuser9 on 2011-03-07
Hey Hedge... I just installed Ubuntu on my computer and my mouse doesn't work at all. I'm on my pocket Ubuntu to come to this forum. Any ideas?

---

### Post by Newuser9 on 2012-03-23
So it's been a while,

I've stopped using my Ubuntu on a stick and want to reclaim the space on it, but I can't seem to delete it and google only tells me how to put it on there.. any ideas?

---

