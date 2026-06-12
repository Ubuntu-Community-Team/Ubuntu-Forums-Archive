---
title: "Error message: &quot;end_request: I/O error, dev sr0&quot;"
date: 2010-07-16
forum: General Help
---

### Post by grindaxe on 2010-07-16
I am using Ubuntu Desktop Edition 10.04 (32 bit). I checked the MD5 checksum of the .iso image before burning it to a disc to make sure that the image wasn't damaged.

I also tested my hard drive with a fairly thorough test to make sure that my hard drive wasn't having problems.

I have Windows 7 already installed on the hard drive. It is taking up a small partition and a larger partition. The larger partition took up the entire drive, so I shrank it to make room for Ubuntu.

I partitioned the drive manually as follows: In the newly created unallocated space (created from shrinking the larger Windows 7 partition), I created 2 more partitions. One was just the swap partition, while the second (for Ubuntu) took up the rest of the unallocated space.

The installation finishes without complaining, but after it is over, I see over 50 lines with the following error (I don't know exactly how many lines there are, but there are so many that they take up more than my entire screen):

[ Some number here] end_request: I/O error, dev sr0, sector (some number here)

The number before "end_request" increases with every row. The number after "sector" also increases, but with every 4 rows. So every 4 lines will have the same sector, but then the next 4 lines will have a different sector number.

If I simply hit enter and restart, the newly installed Ubuntu will start correctly. It also appears to work correctly. I am able to access files on my Windows 7 partition, for example. However, the errors bother me because they seem to indicate that something was wrong with the installation that might cause trouble in the future. The errors just shouldn't be there at all.

I tried to search to see whether this was a known issue, but I didn't find much. For example, I found the following threads:

[http://ubuntuforums.org/showthread.php?t=968194](http://ubuntuforums.org/showthread.php?t=968194)
[http://ubuntuforums.org/showthread.php?t=1015569](http://ubuntuforums.org/showthread.php?t=1015569)

They don't really solve my problem. My hard drive isn't even an IDE hard drive. It's a SATA. I have 2 drives: a DVD rom and a DVD writer. The DVD rom and the DVD writer are on the same IDE cable, but their jumpers are set as master and slave respectively, not cable select.

Does anybody know what might be causing those error messages?

I don't know if this is related, but I also get the following error message before the 50+ lines of errors that I mentioned above:

GLib-warning **:getpwuid_r(): failed due to unknown user id (0)

Thanks for reading.

---

### Post by dcstar on 2010-07-17
> **grindaxe said:**
> 
.........
The installation finishes without complaining, but after it is over, I see over 50 lines with the following error (I don't know exactly how many lines there are, but there are so many that they take up more than my entire screen):

[ Some number here] end_request: I/O error, dev sr0, sector (some number here)
........

Let me guess, you removed the CD before the installation program specifically told you to?

---

### Post by grindaxe on 2010-07-17
> **dcstar said:**
> Let me guess, you removed the CD before the installation program specifically told you to?

No I didn't. I don't even know when to remove the CD until the installation program specifically tells me to. This isn't the problem.

---

### Post by audinutt on 2010-08-19
I had the same issue and ended up having to unplug all memory card readers, and other hard drives, then reinstall with only 1 hard drive and cd-rom and it then worked.

---

### Post by Skidbladnir on 2010-08-19
It's probably just a problem with your cd reader.  If your really nervous, you can take the long(ish) way using the alternate install method.  (Bit of a pain if you don't need to use it...)

---

### Post by audinutt on 2010-08-19
doubt it since both drives i tried to used were less than 2 months old..
It seemed to be a problem with having multiple sata drives connected.

---

### Post by theSshow on 2011-01-04
Anybody find a solution to this problem without having to unplug the hardware. I'm having the exact same problem, but with Windows 7 and 10.10.

Thanks.

---

### Post by Quackers on 2011-01-04
When installing I always get these errors when the cd is ejected, just before it restarts. If I take the cd out, close the drive and hit enter, all is ok. I don't think I'm taking the cd out too early as I wait for the instruction to do so. This has happened every time I have installed Ubuntu (maybe 10 times altogether).
There are no adverse effects at all.

---

### Post by theSshow on 2011-01-04
Hmm. So my cd also gets ejected and at the end when I press "Enter" the computer restarts, but it just hangs and I don't get the grub screen.

---

### Post by theSshow on 2011-01-04
Ok, problem solved.  I just had a faulty CD.  Quackers, you were right, I did get the messages again, but there was no adverse affect at all.  I just tried a new installation CD, and everything installed fine.  Now my machine can dual boot Windows 7 and 10.10!

---

### Post by zieraQ on 2011-02-17
Hi all, this is my 1st post. I encounter the same problem & after restart the grub loader did not appear. just straight away booting into win xp which already installed inside the system. Anybody have any idea how to resolve this? 

btw I use the usb flash method instead of burn the LiveCD iso.

---

### Post by zieraQ on 2011-02-17
could it be because I did not set up partition for swap files? I read about it & afaik it can be set up manually later on......
btw I use the 10.10 version

---

