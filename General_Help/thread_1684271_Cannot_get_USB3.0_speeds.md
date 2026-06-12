---
title: "Cannot get USB3.0 speeds"
date: 2011-02-08
forum: General Help
---

### Post by gmos on 2011-02-08
Just purchased a Samsung Story Station 3 to take advantage of usb3.0 capabilities of my motherboard. However, when transferring my AV files to it the speed was consistently at USB2 rates of up to 30MB/s.

Asrock 890FX Deluxe 3 with 4 rear USB3.0 ports (running a AMD 1055T hex core cpu). USB3.0 is enabled in BIOS.
The USB3.0 onboard controller is a NEC MPD720200.

The ext. drive recognises the usb3.0 ports by showing a blue indicator light, (which is green if connected to a usb2 port).

After a fresh restart and then plugging in the drive:
from "dmesg |grep -i new | tail -5"
[INDENT][    4.184972] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
[    4.205683] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 9
[    6.563535] tuner-simple 0-0061: creating new instance
[   87.240069] usb 5-1: new low speed USB device using ohci_hcd and address 3
[   88.031142] usb 8-2: **new SuperSpeed USB device using xhci_hcd and address** 2[/INDENT]
So it seems all the hardware is recognised and working, but something is preventing it from achieving USB3.0 speeds.

Disk Utility reports that the Samsung is connected at 705Mb/s (up from usual 480Mb/s for usb2 connection) which is a far cry from the 'SuperSpeed' of up to 5Gb/s.

Not happy buying USB3.0 devices to only get a usb2 speed of around 25-30MB/s.

Any ideas of how to get decent USB3.0 speeds?

---

### Post by viktorzk on 2011-02-08
I don't know much about usb, but according to [http://en.wikipedia.org/wiki/USB2](http://en.wikipedia.org/wiki/USB2) , usb2 should achieve over 600MB/s, which suggests that your problem is not with the usb version, but with whatever you are reading from/writing to.
I will be surprised if your external hard drive or usb stick can achieve even 100MB/s.

---

### Post by dcstar on 2011-02-08
> **viktorzk said:**
> I don't know much about usb, but according to [http://en.wikipedia.org/wiki/USB2](http://en.wikipedia.org/wiki/USB2) , usb2 should achieve over 600MB/s, which suggests that your problem is not with the usb version, but with whatever you are reading from/writing to.
I will be surprised if your external hard drive or usb stick can achieve even 100MB/s.

Exactly, the limiting factor is rarely the link connection speed but the devices on either end of it.

People are fools if they believe the advertising that the maximum possible rate of one component of a system means that the whole system goes that fast.

---

### Post by psusi on 2011-02-08
> **viktorzk said:**
> I don't know much about usb, but according to [http://en.wikipedia.org/wiki/USB2](http://en.wikipedia.org/wiki/USB2) , usb2 should achieve over 600MB/s,

No, it does't.  It says 60 MB/s for USB2.  USB3 is supposed to do 600, but neither gets anywhere near that because USB is a terrible protocol.

---

### Post by gmos on 2011-02-09
> **viktorzk said:**
> I don't know much about usb, but according to [http://en.wikipedia.org/wiki/USB2](http://en.wikipedia.org/wiki/USB2) , usb2 should achieve over 600MB/s, which suggests that your problem is not with the usb version, but with whatever you are reading from/writing to.
I will be surprised if your external hard drive or usb stick can achieve even 100MB/s.

Not sure what you're referring to here, that article states "The theoretical maximum data rate in USB 2.0 is 480 Mbit/s (60 MB/s) per controller" , perhaps you're getting bits (b) and bytes (B) mixed up.

I get _up to_ 30MB/s transfer on usb hdd, which is very, very good for USB2!! and I get somewhat less, much less, for usb flash drives. All good and perfectly reasonable.

My issue is with USB3.0.
Have usb3 m/b with usb3 ports transferring to a _usb3 ext hdd_ using a usb3 cable. Of course I know that real transfers will not be anywhere near the theoretical max of 5Gbits/s (over 600MBytes/s), but it would be reasonable to expect it to be faster than my usb2 rates. Even just double usb2 would be fine.

As I previously explained, all the hardware is usb3 rated, enabled and recognised, but just not transferring at anything above my normal usb2 rates.

I don't believe advertised rates are realistic at all ! But I do expect some degree of performance increase with the upgrade! And if someone can offer advice toward addressing the performance issue, I would be most grateful.

---

### Post by dcstar on 2011-02-09
> **gmos said:**
> 
.........
As I previously explained, all the hardware is usb3 rated, enabled and recognised, but just not transferring at anything above my normal usb2 rates.

I don't believe advertised rates are realistic at all ! But I do expect some degree of performance increase with the upgrade! And if someone can offer advice toward addressing the performance issue, I would be most grateful.

If the limiting factor is the disk performance then the USB connection won't matter if it is 400Mb/s or 4,000,000Mb/s.

I believe the protocol overheads via the USB are significant, but if the drive performance was the limiting factor on a USB2 connection then changing to USB3 will not make much - if any - difference.

A car with a small engine going flat out on a 2 lane road will not go any faster on a 10 lane freeway.

---

### Post by P4man on 2011-02-09
Any modern harddrive should be able to break well past 30MB/s if it isnt constrained by the interface. A quick google throws this review:
[http://www.expertreviews.co.uk/external-hard-drives/278278/samsung-story-station-usb-3-0-2tb](http://www.expertreviews.co.uk/external-hard-drives/278278/samsung-story-station-usb-3-0-2tb)

where that same (?) external drive clocks in at around 100MB/s.

The question is, where is the OP copying from or to? The bottleneck might be there. 

gmos, can you run the benchmark utility thats built in ? System > administration > disk utility > select your drive > benchmark.

---

### Post by Grenage on 2011-02-09
> **gmos said:**
> Just purchased a Samsung Story Station 3 to take advantage of usb3.0 capabilities of my motherboard. However, when transferring my AV files to it the speed was consistently at USB2 rates of up to 30MB/s.

Asrock 890FX Deluxe 3 with 4 rear USB3.0 ports (running a AMD 1055T hex core cpu). USB3.0 is enabled in BIOS.
The USB3.0 onboard controller is a NEC MPD720200.

The ext. drive recognises the usb3.0 ports by showing a blue indicator light, (which is green if connected to a usb2 port).

After a fresh restart and then plugging in the drive:
from "dmesg |grep -i new | tail -5"
[INDENT][    4.184972] xhci_hcd 0000:03:00.0: new USB bus registered, assigned bus number 8
[    4.205683] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 9
[    6.563535] tuner-simple 0-0061: creating new instance
[   87.240069] usb 5-1: new low speed USB device using ohci_hcd and address 3
[   88.031142] usb 8-2: **new SuperSpeed USB device using xhci_hcd and address** 2[/INDENT]
So it seems all the hardware is recognised and working, but something is preventing it from achieving USB3.0 speeds.

Disk Utility reports that the Samsung is connected at 705Mb/s (up from usual 480Mb/s for usb2 connection) which is a far cry from the 'SuperSpeed' of up to 5Gb/s.

Not happy buying USB3.0 devices to only get a usb2 speed of around 25-30MB/s.

Any ideas of how to get decent USB3.0 speeds?

Looking at reviews:

> The Story Station sped through all our file transfer tests. Although it isn't quite the fastest USB3 disk we've seen, it was still blisteringly quick. Large files were written at just under 98MB/s and read at 111.9MB/s. Small files were written at a chart-topping 79MB/s and read at 80.3MB/s.

So assuming that the your computer is running ok, and you have remotely modern drives - it should indeed be a lot quicker than 30MB/s.

I know it's not much help now, but I always recommend ESATA for external drives;  USB is a horrible medium for data transfers.

---

### Post by gmos on 2011-02-09
> **P4man said:**
> Any modern harddrive should be able to break well past 30MB/s if it isnt constrained by the interface. A quick google throws this review:
[http://www.expertreviews.co.uk/external-hard-drives/278278/samsung-story-station-usb-3-0-2tb](http://www.expertreviews.co.uk/external-hard-drives/278278/samsung-story-station-usb-3-0-2tb)
.

The question is, where is the OP copying from or to? The bottleneck might be there. 

gmos, can you run the benchmark utility thats built in ? System > administration > disk utility > select your drive > benchmark.

Thanks for that reply P4man, I agree that a new ext hdd, especially a usb3.0 one, should be getting past 30MB/s. I'm copying my multimedia stuff from my /home or backup drives (both Seagate 500GB 7200rpm) to the ext usb3.0 Samsung Story 1TB.

OK, did some read only benchmark tests. 
internal hdd for /home -- min 56  Av 115  max 150 MB/s
internal hdd for backup - min 70  Av 113  max 140 MB/s

Ext Samsung 1TB on USB2 - min 30.8  Av 37.2  max 38.8 MB/s
Ext Samsung 1TB on [B]USB3 - min 78    Av 122   max 148.9 MB/s
[/B]

Then, transferred some files from /home hdd to Samsung using usb3.
A 2.9GB mp4 file transferred at **22-23 MB/s**
Approx 3000 mp3 files transferred at **25-26 MB/s**
(These are about the same transfer rates I get on older usb2 ext hdd. Both Nautilus file operations dialogue and conky hdd monitor show same rates.)

Hope this can provide some more insight

PS - Grenage, yes I considered eSata and perhaps should have chosen it !!

---

### Post by P4man on 2011-02-09
Interesting. The read speeds you are getting using USB3 prove USB3 is working and those speeds are perfectly fine. THe write speeds seem pretty poor though.

If there is no data on the external drive that you need, can you do a write benchmark on the external drive? Either using the benchmark utility that comes with disk utility, or you could do

dd if=/dev/zero of=/dev/yourexternalharddrive

careful, this will wipe the drive!

then run ```
iotop 
```in another window (may need to install that) or just cancel dd after a minute using control+c and see what it reports

Frankly, I suspect the problem with the write speed is due to the fact you are using NTFS on the external drive? THe above would give you full speed no matter the filesystem.

---

### Post by gmos on 2011-02-09
Wow, that was a quick reply P4man.

Gone midnight here. Will do the read/write benchmark tomorrow (though about doing it earlier, but didn't want to wipe drive if I could avoid it).

Will do read/write with NTFS, and then again reformatted as FAT , to see if any difference. 
Will explore and post results asap tomorrow.

Thanks again for your help and suggestions.

---

### Post by P4man on 2011-02-09
FAT may not be a good idea with a 1+TB drive :). Use Ext3 or 4

---

### Post by psusi on 2011-02-09
Do not use /dev/random.  That is for cryptographically strong random numbers and will block until there is enough entropy available, so it can not be used for bulk transfers like that.  If you really want random data for dd, use /dev/urandom, but for a simple throughput test, /dev/zero is fine.

---

### Post by P4man on 2011-02-09
Good point, hadnt thought that through. And even urandom seems surprisingly slow:

bob@HTPC:~$ dd if=/dev/urandom of=/dev/null
119003+0 records in
119002+0 records out
60929024 bytes (61 MB) copied, 14,281 s, **4,3 MB/s**

By comparison:

bob@HTPC:~$ dd if=/dev/zero of=/dev/null
8715428+0 records in
8715427+0 records out
4462298624 bytes (4,5 GB) copied, 7,66906 s, **582 MB/s**

---

### Post by Grenage on 2011-02-09
urandom generates data using algorithms such as SHA, so it's always going to be a lot slower than zero.

---

### Post by gmos on 2011-02-09
Thanks for those replies, much appreciated.

Some interesting results to my exploring/tinkering.

First,
dd if=/dev/zero of=/dev/sdh
2420833+0 records in
2420833+0 records out
1239466496 bytes (1.2 GB) copied, 82.0557 s, 15.1 MB/s

Not sure how significant that result is, but what follows is:

Since drive wiped, reformatted to different file systems and tested transfer speed -

Ext4 
2.9 GB file= **~113MB/s**

NTFS 
2.9 GB file= **~25MB/s**


FAT32 
2.9 GB file= **_~117MB/s_**
2.6 GB file= ~87MB/s
3.5 GB folder= ~113MB/s
6.1 GB folder= ~100MB/s
The drive is to be used to hold AV files for my WDTV HD media player and needs to be either NTFS or FAT32, hence the extra tests on FAT32.

Seems using NTFS is the problem for some reason. It would be great if this could be remedied, but I am still quite satisfied with the FAT32 speeds. What would be the downside, if any, of using FAT on the drive for my AV collection??

---

### Post by HiImTye on 2011-02-09
the only downside other than how it writes (fragmentation) would be file size limitations (I believe it's 4GB-1B)

oh yes, you also can't set user permissions on FAT but the operating system has to honor them anyway

---

### Post by 3rdalbum on 2011-02-09
> **gmos said:**
> 

Seems using NTFS is the problem for some reason. It would be great if this could be remedied, but I am still quite satisfied with the FAT32 speeds. What would be the downside, if any, of using FAT on the drive for my AV collection??

NTFS writing is slow on Linux, due to the (legally-safe) way it is implemented: in user-space rather than in the kernel.

Unfortunately, FAT has a file-size limit of 4 GiB which is not really enough for movies in Full HD.

Are you sure the WD TV doesn't accept other filesystem formats? I have a similar sort of device that accepts Ext3.

---

### Post by P4man on 2011-02-10
Good to see USB3 is working as it should.

NTFS having slow write speeds is a known issue. Not sure what legally-safe has to with it (care to enlighten us?) but its CPU heavy for writes. You might want to have a look here:
[http://www.tuxera.com/community/ntfs-3g-faq/#slow](http://www.tuxera.com/community/ntfs-3g-faq/#slow)

Tuxera is the company that writes the ntfs-3g driver. Most of the remarks there are somewhat lame "excuses" IMHO, but some tips in there might be useful, like aligning the partition.

As for other filesystems; well its the eternal tradeoff to be made. You cant have it all, good performance, cross platform and support for large files. Perhaps the easiest solution for you is using fat32 and split the movies larger than 4GB, assuming your media player handles multi file movies gracefully.

---

### Post by gmos on 2011-02-10
Once again thanks.

Will stick to FAT32 as the file system, as I don't have any mp4s over 3GB in size and am getting 4-5 times my usb2 rates.

WDTV HD player only supports NTFS, FAT and HFS+ - there is a custom firmware that gives ext2/3 support, but I'd prefer not to.

I suppose this is less of a solution than a good work around- but am happy to get the performance from the hardware I paid extra for.
I am surprised that NTFS + usb3 problem is not well known - or perhaps it's just a quirk of my particular system/setup.

Consider as solved !

---

### Post by P4man on 2011-02-10
> I am surprised that NTFS + usb3 problem is not well known - or perhaps it's just a quirk of my particular system/setup.

its not the combination of USB3+NTFS, its just writing to NTFS in general (from linux) thats relatively slow, and its pretty well known.  But since 30MB/s is faster than most NAS boxes or USB drives can deliver anyway, few people notice or complain.

---

