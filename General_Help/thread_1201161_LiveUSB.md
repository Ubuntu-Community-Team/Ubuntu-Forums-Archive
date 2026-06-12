---
title: "LiveUSB?"
date: 2009-06-30
forum: General Help
---

### Post by valikor on 2009-06-30
This is probably a very basic question, but I can't find instructions anywhere.

I'm trying to optimize the performance on my new Dell Mini 12, and I wanted to give Xubuntu a try. I've heard mixed things, so I'd prefer to use a LiveCD to give it a test run and see if it helps my performance.

Of course, the mini 12 doesn't have a CD Rom drive, so can I do something equivalent with a USB external HD? 

Thanks!

David

---

### Post by t4thfavor on 2009-06-30
boot the livecd on a real pc with a cdrom, and go to system -> administration -> and then select USB startup disk.

you will need a 1GB or bigger for the job, and it will actually let you save things to the usb like preferences, and user files.

---

### Post by Mighty_Joe on 2009-07-01
The LiveCD-on-usb will not be representative of the performance of Xubuntu.  The LiveCD is a 700Mb compressed live file system and decompressing it to RAM adds considerably to memory use and CPU load.  If you want a more realistic comparison, you can install Xubuntu directly onto a flash drive (if it's 4GB+, make sure you install Grub on the flash drive too or it won't boot).  There's other optimizations for Ubuntu flash drives.  See my post [over here]("http://ubuntuforums.org/showthread.php?t=1193680")

---

