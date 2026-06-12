---
title: "Ubuntu will not boot"
date: 2010-11-17
forum: General Help
---

### Post by suver.17 on 2010-11-17
I have a Dell mini 10 netbook appx 1.5yrs old.  It was working fine one night, however the next day I went to use it and it will not boot.  When powering on, it goes through the dell screen, allowing me to access the boot options/bios screens.  It then hits the Ubuntu screen with the loading bar, and it just sits there.  The bar does not load at all and nothing else is able to be done.

As this is a netbook, there is no cd drive.  It came from dell with ubuntu installed already.  I have made a usb bootloader from an external hard drive using the most current netbook remix version of ubuntu.  I was going to use this to boot the computer from and then install the new version of the operating system.  I have changed the boot options of the computer to have booting from a usb device as a top priority, however when trying to do this, the computer does the same thing and when it hits the Ubuntu boot screen it just sits there.

Does anyone have any insight on what is wrong or how to fix this issue?  Please keep in mind that I am relatively inexperienced with this type of stuff.

---

### Post by lmarmisa on 2010-11-17
I would like to know if your USB bootloader (external hard drive) is a full Ubuntu Remix installation able to run in any computer.

---

### Post by suver.17 on 2010-11-17
i'm not sure, as I said I dont have much experience with this.  My main computer is an iMac, so I'm not sure how to tell.

---

### Post by lmarmisa on 2010-11-17
Did you install Ubuntu Remix in your external USB drive?. What version?.

---

### Post by suver.17 on 2010-11-17
Yes, version 10.10 I believe, the most recent version available to download, using the instructions on creating the USB drive for Mac.  ([http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download))

---

### Post by lmarmisa on 2010-11-17
Sorry, I have no experience with Mac. So, I am not sure I could help you.

Anyway, two questions:

[LIST=1]
[*]Do you have an external USB CD/DVD drive?
[*]Are you able to boot your Ubuntu Remix 10.10 (installed in the external USB hard drive) in you Mac computer?
[/LIST]

---

### Post by suver.17 on 2010-11-17
Unfortunately, I do not have a USB cd/dvd drive.  I have not tried booting it to my mac yet via usb, however, quick searches make it seem like it may not work.  I'll have to give it a shot.  I'm wondering if the issue is software related, or if there is maybe a hardware issue.

---

### Post by lmarmisa on 2010-11-17
I suppose you have no other PC with Linux or Windows.

---

### Post by suver.17 on 2010-11-17
unfortunately not.  I'll have to try to find someone with a windows computer available to give my usb drive a try.

---

### Post by lmarmisa on 2010-11-17
I understand that you have installed Ubuntu in a USB hard drive, not a pendrive. However the instructions of that installation page seem oriented to pendrives.

I have a 2.5'' USB hard drive that I use mainly for backups. I decided to make a full Ubuntu installation in this drive. I defined 3 partitions: a big NTFS partition for my backups; a 10 Gbytes EXT4 partition for Ubuntu; and finally a 1 Gbyte swap partition. I made a standard installation selecting manually partitions #2 and #3 and, very important, during the installation I selected the option for storing the GRUB loader in this external USB drive (do not use /dev/sda for the GRUB loader in this type of installations!!!).

So, I use this 2.5'' USB drive when I need to boot Ubuntu in any computer with some problem. This is really a much better solution than a LiveCD or a pendrive with Ubuntu.

---

