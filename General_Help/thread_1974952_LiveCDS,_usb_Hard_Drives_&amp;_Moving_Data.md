---
title: "LiveCDS, usb Hard Drives &amp; Moving Data"
date: 2012-05-06
forum: General Help
---

### Post by tinker123 on 2012-05-06
Hi;

Last night I upgraded from Ubuntu 10.10 -> Ubuntu 12.04.  Things worked okay for a while, but now I can't boot up my computer at all with Ubuntu 12.04.

Luckily, I had a livecd of an old copy of XUbuntu, so I can at least get on the internet to ask for help.

My plan is to buy a usb harddrive tomorrow and use the livecd to copy my data over.  Then I'm going to reinstall from scratch.

If I plug the USB drive into my PC before booting the livecd of Xubuntu 10.10, will that hard drive be detected?

Will I have to do any special commands to access it or my regular hard drive to copy files over?

Thanks in advance for any tips.

---

### Post by mendhak on 2012-05-06
> If I plug the USB drive into my PC before booting the livecd of Xubuntu 10.10, will that hard drive be detected?

Yes, but it shouldn't matter when you plug it in.  You should be able to plug the USB drive in after booting into Live USB too.  I have done this in the past for the same purpose of copying files over to a backup drive.

Could you try it right now, with some other USB device like a pen drive or mount your phone?

---

### Post by tinker123 on 2012-05-06
Yep. I just plugged a thumb drive in and it detected everything automatically.  How do I get Xubuntu to see my hard drive?

---

### Post by tinker123 on 2012-05-09
I found my own answer, but I thought I would post for other people having the same problem.

More modern livecds may do all of this automatically, but I was stuck in an emergency situation with an copy of Xubuntu 10.10.

A set of commands like this will tell you what the hard drive is called:

> 
$ sudo bash
$ fdisk -l


It will be something like /dev/sda1

To mount it so that the livecd file manger can see the hard drive do something like this:

> 
$ sudo bash
$ mount /dev/sda1  /mnt/harddrive


I bought an external harddrive to rescue my data in conjunction with Xubuntu 10.10.  I was impressed with the deal.  For $140 I got a drive the size of my hand that holds a terabyte.  It only had to be hooked into the USB port to get both the data and its power.  It also works with either PCs or Macs.  I didn't even have to format it.  All I had to do was reboot the livecd of Xubuntu 10.10 after plugging it in for it to be seen.  Very nice.

---

