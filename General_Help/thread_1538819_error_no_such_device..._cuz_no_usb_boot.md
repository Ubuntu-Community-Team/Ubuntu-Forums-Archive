---
title: "error: no such device... cuz no usb boot"
date: 2010-07-25
forum: General Help
---

### Post by angel34160 on 2010-07-25
Hi I'm new at this just 3 days with unbuntu and I just broke my lap :sad:

I have a Hp 2133 and a external hard drive western digital 80G connected  by usb  what i tried to do was use the 80G HD with unbuntu and the 160G  internal with Win xp as usual but now appear the error no such device  and just the message 

error: no such device: xxxxxxx
grub rescue> _ 

I installed the unbuntu by usb in the external HD 80G  also  is a usb but now on  the bios optiopn no usb boot option appear and i can't run the installer  again  just the internal HD and netboot options the lap top don't  include cd room so can't run the win setup  cd try the comand that say on [http://ubuntuforums.org/showthread.php?t=1538228](http://ubuntuforums.org/showthread.php?t=1538228)  only 

>_  ls                            work 
(hd0)  (hd0,1)  (fd0)

and I'm really a new one at this so any response make it in a way easy  to understand (with draws will be great :grin:)   any idea?

Thnaks

---

### Post by C.S.Cameron on 2010-07-25
Without a CD drive it is hard to run a XP install CD and start Emergency Repair Console to do a "fixmbr".
Can you borrow a USB CD drive?
When installing to an external USB drive you should select the Advanced option after partitioning and make sure grub is installed only on the external drive.

I have previously used ms-sys to fix XP boot records destroyed by Ubuntu:

[http://packages.ubuntu.com/dapper/i386/ms-sys/download](http://packages.ubuntu.com/dapper/i386/ms-sys/download)

---

### Post by angel34160 on 2010-07-25
Thank you for the Reply ;)

Is not posible because the lap is a mini don't include CD rom or DVD rom is nesesary use a external by usb and is not detecting usb thats why i can't run the set up usb memory  again to install in the internal HD it doesn't matter to loose all the data just need to recover the laptop cuz it don't start  :(

---

