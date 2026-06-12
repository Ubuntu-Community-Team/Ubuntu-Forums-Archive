---
title: "can't eject cdrom (yes, it's unmounted)"
date: 2009-08-05
forum: General Help
---

### Post by Xorlium on 2009-08-05
Hi,

For some reason I can't eject the cdrom. I tried everything (by 'everything' I mean the button and writing eject). I can eject from bios (when the computer is starting) but not once I'm in ubuntu, whether the disk is mounted or not. /var/log/messages says this:

```
Aug  5 19:56:29 persefone kernel: [  101.816156] ata2: hard resetting link
Aug  5 19:56:34 persefone kernel: [  107.176097] ata2: link is slow to respond, please be patient (ready=0)
Aug  5 19:56:39 persefone kernel: [  111.824083] ata2: hard resetting link
Aug  5 19:56:44 persefone kernel: [  117.184070] ata2: link is slow to respond, please be patient (ready=0)
Aug  5 19:56:49 persefone kernel: [  121.832083] ata2: hard resetting link
Aug  5 19:56:54 persefone kernel: [  127.196073] ata2: link is slow to respond, please be patient (ready=0)
Aug  5 19:57:24 persefone kernel: [  156.876088] ata2: limiting SATA link speed to 1.5 Gbps
Aug  5 19:57:24 persefone kernel: [  156.876093] ata2: hard resetting link
Aug  5 19:57:29 persefone kernel: [  161.900091] ata2.00: disabled
Aug  5 19:57:29 persefone kernel: [  161.900113] ata2: EH complete
Aug  5 19:57:29 persefone kernel: [  161.900180] sr 1:0:0:0: [sr0] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Aug  5 19:57:29 persefone kernel: [  161.900233] sr 1:0:0:0: [sr0] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
Aug  5 19:57:29 persefone kernel: [  161.900327] sr 1:0:0:0: [sr0] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
```

I'm using kubuntu 9.04, ext4, 64-bit. I did a fresh install of the system (I had some problems, so I had to reinstall), but it didn't work on the previous version either (same thing exactly), and I'm fully up to date, using kernel 2.6.28-15.

It's a laptop Asus G50VT

The strangest thing is that if I open the tray at bios, and then wait, log into the system, place a dvd, then close it, it IS able to read it.

Any ideas?

Thanks!

Edit: I forgot to mention I did try the sudo hal-something disable polling thingy mentioned in the FAQ. It doesn't help either. This time I got more things:
```

[   59.816093] ata2.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x6 frozen                               
[   59.816111] ata2.00: cmd a0/01:00:00:00:10/00:00:00:00:00/a0 tag 0 dma 4096 in                             
[   59.816114]          cdb 28 00 00 00 00 38 00 00  02 00 00 00 00 00 00 00                                  
[   59.816116]          res 40/00:03:00:fe:00/00:00:00:00:00/a0 Emask 0x4 (timeout)                           
[   59.816122] ata2.00: status: { DRDY }                                                                      
[   59.816131] ata2: hard resetting link                                                                      
[   65.176126] ata2: link is slow to respond, please be patient (ready=0)                                     
[   69.824574] ata2: COMRESET failed (errno=-16)                                                              
[   69.824586] ata2: hard resetting link                                                                      
[   75.184080] ata2: link is slow to respond, please be patient (ready=0)                                     
[   79.832099] ata2: COMRESET failed (errno=-16)                                                              
[   79.832112] ata2: hard resetting link                                                                      
[   85.196096] ata2: link is slow to respond, please be patient (ready=0)                                     
[  114.876054] ata2: COMRESET failed (errno=-16)                                                              
[  114.876062] ata2: limiting SATA link speed to 1.5 Gbps
[  114.876066] ata2: hard resetting link
[  119.900099] ata2: COMRESET failed (errno=-16)
[  119.900110] ata2: reset failed, giving up
[  119.900115] ata2.00: disabled
[  119.900140] ata2: EH complete
[  119.900214] sr 1:0:0:0: [sr0] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  119.900223] end_request: I/O error, dev sr0, sector 224
[  119.900230] Buffer I/O error on device sr0, logical block 28
[  119.900271] sr 1:0:0:0: [sr0] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  119.900278] end_request: I/O error, dev sr0, sector 232
[  119.900283] Buffer I/O error on device sr0, logical block 29
[  119.900288] Buffer I/O error on device sr0, logical block 30
[  119.900294] Buffer I/O error on device sr0, logical block 31
[  119.900299] Buffer I/O error on device sr0, logical block 32
[  119.900305] Buffer I/O error on device sr0, logical block 33
[  119.900310] Buffer I/O error on device sr0, logical block 34
[  119.900315] Buffer I/O error on device sr0, logical block 35
[  119.900320] Buffer I/O error on device sr0, logical block 36
[  119.900325] Buffer I/O error on device sr0, logical block 37
[  119.900346] sr 1:0:0:0: [sr0] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  119.900355] end_request: I/O error, dev sr0, sector 1024
[  119.900411] sr 1:0:0:0: [sr0] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  119.900417] end_request: I/O error, dev sr0, sector 1024
[  119.905897] sr 1:0:0:0: [sr0] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  119.905906] end_request: I/O error, dev sr0, sector 512
[  119.905944] sr 1:0:0:0: [sr0] Result: hostbyte=DID_BAD_TARGET driverbyte=DRIVER_OK,SUGGEST_OK
[  119.905951] end_request: I/O error, dev sr0, sector 512

```

---

### Post by Xorlium on 2009-08-06
bump

---

### Post by Claus7 on 2009-08-06
Hello,

no kubuntu here, not even the same problem faced in the past. Some questions though:
how were you able to have the latest kernel installed? As far as I know, till the time I'm writing, (k)ubuntu supports the 2.6.28-14 kernel. I mean, did you compile the kernel by yourself and this caused some issues?

For some reason it seems that your dvd is not recognised. Have you checked your cables? 

Yet, what is a mystery is that if you have the tray open at boot then the dvd is recognised. 

So, can you insert a dvd while logged at kubuntu (open and close the tray) ?
If you do that can you read it?
Either being able to read it or not, the fact is that you cannot eject it. Yet, can you see any messages while the dvd is inside?
Can you access the dvd via /media/dvd-something while from terminal?

How did you unmount the disk? Were you root? Even if you unmount the disk, in order to eject it, you have to press the button (I think)...

Sorry, yet these are the things I can think of. Maybe someone else can help you better.

EDIT: If I were in your shoes, I would try to insert also a dvd that it would be written under kubuntu and check this out. In other words I would try other dvds as well.

Regards!

---

### Post by Shazaam on 2009-08-06
Try this...
```
sudo eject
```

---

### Post by Xorlium on 2009-08-06
Hi,

Thanks for the replies. Here are my counter-replies:

I've tried eject and sudo eject and sudo su eject and all that :) I'm not a complete newbie.

Oh, and I forgot to mention that it does work under windows (the computer has dual-boot).

> no kubuntu here, not even the same problem faced in the past. Some questions though:
how were you able to have the latest kernel installed? 
As far as I know, till the time I'm writing, (k)ubuntu supports the 2.6.28-14 kernel. I mean, did you compile the kernel by yourself and this caused some issues?
I selected unsupported updates too. But I tried with the kernel 2.6.28-14 and it's exactly the same story. I didn't compile it on my own :)

> For some reason it seems that your dvd is not recognised. Have you checked your cables?
Well, it's a laptop, so no cables to check. Also, why does it work under windows?

> Yet, what is a mystery is that if you have the tray open at boot then the dvd is recognised.
I forgot to mention that it SOMETIMES woks, not always. But if i try doing anything other than copying the files or something, it stops working forever and dmesg says "ata2 device disabled". So if I try to unmount or eject or whatever, it stops working right there.

> So, can you insert a dvd while logged at kubuntu (open and close the tray) ?
Nope. The tray doesn't open inside ubuntu, with or without a dvd inside.

> 
Either being able to read it or not, the fact is that you cannot eject it. Yet, can you see any messages while the dvd is inside?

No

> Can you access the dvd via /media/dvd-something while from terminal?

No, I can't. I tried mounting and unmounting by mount /dev/sr0 /media/cdrom and all that, but it just doesn't do anything.

> How did you unmount the disk? Were you root? Even if you unmount the disk, in order to eject it, you have to press the button (I think)...

I've tried it as both, root and not root, and with the little button in the device notifier and directly from the terminal.

> EDIT: If I were in your shoes, I would try to insert also a dvd that it would be written under kubuntu and check this out. In other words I would try other dvds as well.
Uh... what? :)

---

### Post by warp99 on 2009-08-06
Here's your issue and a workaround:

[http://ubuntuforums.org/showpost.php?p=7580427&postcount=5](http://ubuntuforums.org/showpost.php?p=7580427&postcount=5)

Next time please search the forums before you post since I found the answer in roughly 30 seconds.

---

### Post by Xorlium on 2009-08-06
Oh. Thanks! :) It works now!

I did search the forum, and read the FAQ, apparently not well enough. I searched " eject cdrom" and read many posts, but never got to that one. I should have searched Asus G50.

It's strange. For 8.10 I had to install it like that (setting it to compatible mode). But then I read somewhere that a kernel update fixed it, so I switched back to enhanced mode. When I installed 9.04, I had no problems with this. 

Apparently the kernel broke it again... or what?

---

