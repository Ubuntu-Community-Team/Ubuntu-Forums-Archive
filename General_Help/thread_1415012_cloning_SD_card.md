---
title: "cloning SD card"
date: 2010-02-24
forum: General Help
---

### Post by bixejo on 2010-02-24
Hi there,

I'm trying to clone a SD card device. It only has one filesystem, but I'd like to copy the whole device so that partition table and MBS are also copied. Device is /dev/mmcblk0, and its only filesystem is  /dev/mmcblk0p1.

I tried the following three methods:

[SIZE=2]**Method 1:**[/SIZE]
```
# cat /dev/mmcblk0 > attempt1.iso
```[SIZE=2]**Method 2:**[/SIZE]
```
# dd bs=512 if=/dev/mmcblk0 of=attempt2.iso
```[SIZE=2]**Method 3:**[/SIZE]
 ```
# dd bs=32768 if=/dev/mmcblk0 of=attempt3.iso 
``` And it seems that all succeeded:

```
# file attempt*
attempt1.iso: x86 boot sector, extended partition table (last)\011
attempt2.iso: x86 boot sector, extended partition table (last)\011
attempt3.iso: x86 boot sector, extended partition table (last)\011
# ls -l attempt*
-rwxrwx--- 1 root plugdev 3959422976 2010-02-24 15:09 attempt1.iso
-rwxrwx--- 1 root plugdev 3959422976 2010-02-24 14:51 attempt2.iso
-rwxrwx--- 1 root plugdev 3959422976 2010-02-24 13:52 attempt3.iso
```

[SIZE=2][COLOR=Red]**BUT**[/COLOR][/SIZE] look:

```
$ md5sum attempt*
43ece884372dbe14091ef0c16d73b0c5  attempt1.iso
9454b9f49f93cecf76418f773bd79c75  attempt2.iso
4f75e643e18aedcd895d2cf9fbe5d2b2  attempt3.iso
```So, which one is the right one, and why they are different?? :confused::confused:

Thank you in advance,

---

### Post by dabl on 2010-02-24
You said "clone", but then you gave your output file a different name.  AFAIK, "dd" will (with appropriate options) _clone_ it if you have two identical partitions, but you can't change _anything_.

---

### Post by bixejo on 2010-02-24
Hi dabl,

Thank you for your reply. I probably did not use the right term. When I said "clone" I meant creating an image so that the whole device structure (MBS, partition table, and filesystem(s)) could be recreated by using the reverse method:

For the 1st case:
```
cat attempt1.iso > /dev/mmcblk0
```For the 2nd case:
```
dd bs=512 of=/dev/mmcblk0 if=attempt2.iso
```, and for the 3rd case:
```
dd bs=32768 of=/dev/mmcblk0 if=attempt3.iso
```In either case, I believe (wrongly perhaps) that all images should be exactly the same, but they are not.

Hope it's clear now.

Regards and thanks for your help,

---

### Post by lavinog on 2010-02-24
was the filesystem mounted at the time?

I am not familiar with /dev/mmcblk0 my sd cards show up as /dev/sd# where # is a letter

---

### Post by dabl on 2010-02-24
Possibly your use of the ".iso" file type is not appropriate for dd.  Look at this: [http://www.brighthub.com/computing/linux/articles/38387.aspx?p=3](http://www.brighthub.com/computing/linux/articles/38387.aspx?p=3)

---

### Post by bixejo on 2010-02-24
Thank you both for your kind replies.

Of course, the filesystem was not mounted when I made the device copy in any of the three cases.

I believe that the ".iso" part and the whole file name are irrelevant for how dd writes data. Anyhow, thank you for the tip and for the suggested link.

I'll keep on trying. Any other help or suggestion shall be welcome.

Regards,

---

### Post by lavinog on 2010-02-24
dd doesn't care what the file extention is...you can use .doc if you wanted to [just don't double click it ;)]

It seems that the difference is solely caused by the block size.

one way to tell would be to use the same block sizes again and check the md5s.  If you get the same md5s, then that verifies it is caused by the block size.
I have yet to figure out the implications of using different block sizes.  The way gparted will copy partitions by testing various block sizes seems to be only a speed concern.

What is the purpose of cloning the card?  Have you transfered the iso to another card yet to see if behaves as expected?

---

### Post by lavinog on 2010-02-24
I prefer using dd_rescue (the package name is ddrescue) for making images
it gives you a status of the operation.  I also tried various blocksizes of a drive and got matching md5sums.

give it a try and see if it matches any of the above.

---

### Post by bixejo on 2010-02-24
I already did what you suggest. Using the same block size I get the same md5 checksum. Well, I tried it just once, but I believe that's relevant. If it's just a block size issue, as it seems to be, the difference (if any) should be at the end of the file, when dd tries to read one more block and finds less data than expected. But then, the difference should be near the end, and not at the beginning:

```
$ cmp attempt2.iso attempt3.iso
attempt2.iso attempt3.iso are different: byte 4195305, line 1
```The purpose is just to be able to make tests with that card having a restore point to fall back if everything I do go too bad. I haven't tried to dump any of these files to another card as I don't have any other to try, and I don't dare to do it to this one as I do not completely rely on any of these copies...

:-k I'm really confused.

Thank you very much anyhow,

---

### Post by lavinog on 2010-02-24
It could be that the card is not able to retain data anymore.
How old is the card?

My 4g Lexar usb flash drive is only 3 years old, and data is starting to become corrupted.  I can no longer save files to it and expect to get the same data back.

---

### Post by sgosnell on 2010-02-24
Probably what you want is something like mondo or remastersys.  They are designed to make backup .iso files from a filesystem, ready for restoration.  Mondo is very versatile and may be what you need.

---

### Post by dabl on 2010-02-24
> **lavinog said:**
> dd doesn't care what the file extention is...you can use .doc if you wanted to [just don't double click it ;)]



I agree that is true.  But, my concern was (and is), just because you write data, via dd, to a file named "x.iso" does not arrange the filesystem and data correctly per the ISO 9660 standard:

[http://en.wikipedia.org/wiki/ISO_9660](http://en.wikipedia.org/wiki/ISO_9660)

Right?

So (and I admit this whole topic is pretty much above my knowledge level) is there any good reason to think that the "attempt3.iso" (or any other attempt made this way) is going to result in a valid ISO image file?

---

### Post by bixejo on 2010-02-24
> **lavinog said:**
> It could be that the card is not able to retain data anymore.
How old is the card?It's just three days old. I bought it last monday, so I guess that's not the problem.

> **dabl said:**
> I[...] So (and I admit this whole topic is pretty much above my knowledge level) is there any good reason to think that the "attempt3.iso" (or any other attempt made this way) is going to result in a valid ISO image file?No, there is not any reason good or bad, that's true. In fact it's not a filesystem image but a _device_ image, which contains not only the filesystem itself, but also the master boot sector and the partition table. That's at least what it should contain.

As for the other suggested software for backing up filesystems, as I already said I'm not only interested in the filesystem but in the _whole device_.

Many thanks to you all for your help, tips, and suggestions. I'll keep on trying.

---

### Post by sgosnell on 2010-02-24
Both remastersys and mondo back up the whole device, everything, to an .iso which can be restored to a completely workable system.  They're designed to produce .iso files, while dd is not.  But if you insist on doing it your way regardless, then have fun.

---

### Post by lavinog on 2010-02-24
> **sgosnell said:**
> Both remastersys and mondo back up the whole device, everything, to an .iso which can be restored to a completely workable system.  They're designed to produce .iso files, while dd is not.  But if you insist on doing it your way regardless, then have fun.

Those tools do not clone devices...they convert a filesystem to an iso.
They will not backup any deleted files, and they can take longer to restore.

The OP has an interesting point though, the md5s should match...I am curious why they don't.

---

### Post by sgosnell on 2010-02-24
They do what he wants, which is to back up everything, even partitions.  Mondo will let you restore the exact partitions, or to different partition settings if you need to do that.  It does more than dd, and will backup and restore the partitions and write its own kernel if you want.  Read the docs.

If the filesystem was mounted when the backups were made, the md5sums will almost certainly be different.  Any write at all to any file will change them.

---

### Post by lavinog on 2010-02-24
it wasn't mounted.

---

### Post by bixejo on 2010-02-25
> **sgosnell said:**
> Both remastersys and mondo back up the whole device, everything, to an .iso which can be restored to a completely workable system.  They're designed to produce .iso files, while dd is not.
Thank you for the info :smile: . I'll probably give it a try, though dd has proved to be more than enough for my purposes, as I say at the end of this post.

> **sgosnell said:**
> But if you insist on doing it your way regardless, then have fun.There is no need to be sarcastic :neutral: . I didn't know what you said in this post. All I knew so far of all of this is way you said formerly:

> **sgosnell said:**
> Probably what you want is something like mondo or remastersys. They are designed to make backup .iso files from a filesystem, ready for restoration. Mondo is very versatile and may be what you need.And here you talk about files and filesystems, but you don't say anything related to backing up whole devices.

By the way, looks like everything was a problem in my computer card reader. I tried the same thing with another computer (much smaller, cheaper, and slower) and everything went fine; all files were exactly the same when compared with cmp and checked with md5sum and sha256sum.

Also, I went ahead touching the filesystem and the device info, I nuked everything #-o (as I already expected), made the device restoration with dd using the inverse process, and everything got back to its initial state, just like if nothing had been touched =D> .

I've got nothing against mondo or similar stuff (among many other reasons, because I don't know it), but I believe that the simplest things are the best ones (provided that they work, of course). Command dd is available just booting from any Linux live media, making the restoring job much easier to be made as it does not require to have installed any extra stuff, and can even be used from command line with no need of graphical desktop.

Best regards and thank you all very much for all your help and all what I learned from you, \\:D/

---

### Post by lavinog on 2010-02-25
> **bixejo said:**
> 
By the way, looks like everything was a problem in my computer card reader. I tried the same thing with another computer (much smaller, cheaper, and slower) and everything went fine; all files were exactly the same when compared with cmp and checked with md5sum and sha256sum.

Good thing you checked those md5sums then.
Do you know if you got any messages in dmesg about read errors when using that card reader?

---

### Post by bixejo on 2010-02-25
> **lavinog said:**
> Good thing you checked those md5sums then.
Do you know if you got any messages in dmesg about read errors when using that card reader?
I know I didn't get any message. That's something I already checked. It's weird...
 
Now I do get error messages (error -101, if I remember right), but now I cannot even read anything or mount the filesystem either. Probably it began to get broken just at the point I was trying to make the copies first time. It could be just a bit of dust... I believe this is the first time I use the card reader in about two and half years I've had this laptop... :redface:

---

