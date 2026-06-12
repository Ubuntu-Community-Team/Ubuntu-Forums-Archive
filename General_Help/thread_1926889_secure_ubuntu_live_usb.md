---
title: "secure ubuntu live usb"
date: 2012-02-17
forum: General Help
---

### Post by sanchini on 2012-02-17
Hi guys.

I required an operating system on a usb, which can be bootable by a macbook air (and preferably other laptops and PCS, but the macbook is vital).

I require the system to be writable, not like the old live distros I used to have. I need to save emails, bookmarks, install software etc.

Ideally I need it with decent security, it will contain sensitive documents for my work, I'd like it encrypted.

If at all possible I'd like to make it from my macbook air here without installing ubuntu, i.e. get a base system to the flash drive and then perfect it from there, load up my own scripts and configs etc.

Security is important for me.

I was thinking about using a corsair 8G usb drive for this. It has been some time since I played with systems like this but I'm certainly not a newbie.

Please help! If another distro is more suited (especially regards FS encryption) please advise, though I'd prefer ubuntu. Can someone point me at what to do?

Many thanks!

---

### Post by haqking on 2012-02-17
> **sanchini said:**
> Hi guys.

I required an operating system on a usb, which can be bootable by a macbook air (and preferably other laptops and PCS, but the macbook is vital).

I require the system to be writable, not like the old live distros I used to have. I need to save emails, bookmarks, install software etc.

Ideally I need it with decent security, it will contain sensitive documents for my work, I'd like it encrypted.

If at all possible I'd like to make it from my macbook air here without installing ubuntu, i.e. get a base system to the flash drive and then perfect it from there, load up my own scripts and configs etc.

Security is important for me.

I was thinking about using a corsair 8G usb drive for this. It has been some time since I played with systems like this but I'm certainly not a newbie.

Please help! If another distro is more suited (especially regards FS encryption) please advise, though I'd prefer ubuntu. Can someone point me at what to do?

Many thanks!

USB with persistence.

Or install direct to the USB device, everything is the same regardeless of it being on a USB device.

---

### Post by sanchini on 2012-02-17
I thought there were issues with encrypting the home directory when using persistence on USB systems? Is this not the case?

---

### Post by sanchini on 2012-02-17
should add - I really would like pre-boot authentication. Is this possible?

---

### Post by efflandt on 2012-02-17
You do NOT want bootable install iso on USB with persistence if you want security.  That allows anyone who boots it to do anything without password.

Do a regular install to the USB device, and make sure that you also put grub on that USB device instead of default to your internal drive.  So instead of having install do any automatic partitioning, you want to select "Other", so you can select where to install grub.

I know nothing about encrypting Linux partitions, so not sure what is required for that (maybe separate /boot partition?).

---

### Post by snowpine on 2012-02-17
Just do an encrypted full install to the USB stick. (8gb will be tight; the Wiki recommends 15gb minimum). It's been a long time since I did an Ubuntu install, but IIRC you need the Alternate CD for an encrypted install.

It will be slow, and you must be **very sure** when installing that you a) install to the correct drive; b) install GRUB to the correct drive. If you don't understand exactly what this means, then the safe thing to do physically disconnect your internal hard drive (so the USB is the only drive attached).

---

### Post by s3a on 2012-02-17
Install preload; that might help for performance.

---

### Post by sanchini on 2012-02-19
thanks for replies.

OK - made some progress. First - I need this to work on a macbook air. Google shows these are especially hard to make work.

afetr tryinglots of ubuntu directions I tried this:

[http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/](http://studyblast.wordpress.com/2011/08/14/guide-mac-os-x-lion-how-to-boot-a-linux-live-system-from-a-usb-drive-how-to-update-any-ocz-ssds-firmware/)

by manually adding a file to the usb with the iso. For some reason, it seemed to hnag while loading the kernal, perhaps coincidence but after some more fooling around, and a different iso, and with the rEFIt installed, I got it to load to an ubuntu desktop. But now I cannot get persistence.

Does anyone know how to add this?

Thanks, I'll build it up a step at a time.

---

