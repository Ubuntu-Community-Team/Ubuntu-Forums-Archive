---
title: "Repairing/reformatting USB drive"
date: 2011-06-03
forum: General Help
---

### Post by robbiemacg on 2011-06-03
I'm having difficulty repairing/reformatting a USB drive. I'm stumped and feeling foolish, but I haven't much experience with file systems, so maybe one of you can suggest a solution I've yet to explore and get me on the right track. I'm sure I'm missing something obvious.

I have a generic USB drive, 4GB, currently formatted FAT. I can't save files to it, can't format it using Ubuntu's Disk Utility. Attempts to format using Disk Utility return the following error:

Error creating partition table: helper exited with exit code 1: Error calling fsync(2) on /dev/sdb: Input/output error

Yesterday I got fed up and tried to just zero the thing out using a **dd** command... ran it in verbose, the right stuff returned to screen, still no dice. I can't get it to a point where I can format it either using Disk Utility or **mkfs**. Your suggestions are welcome.

Thanks,
Robbie

---

### Post by mike555 on 2011-06-03
Try putting it in a Windows computer then format and properly extract.......  don't just yank it out like so many people do.

---

### Post by linkageless on 2011-06-03
I had a similar situation with an SDHC card in a reader which turned out to be a poor contact to the write enable contact on the card. Not saying that this is the case here though, but have you been able to successfully write anything to the device?

After your dd does the drive still appear unchanged to fdisk?

---

### Post by robbiemacg on 2011-06-03
Thanks for your replies, friends.
[mike555]("http://ubuntuforums.org/member.php?u=107656") : I'm hoping to solve this problem at home, where only Linux is permitted... but I'll take a look at the disk at work if worse comes to worst. 
[linkageless]("http://ubuntuforums.org/member.php?u=603799") : I have written to the device in past. Haven't been able to write to it recently. (This drive was shared with a less savvy colleague recently. I'm not sure how it was treated.)
I can still **ls** hidden files referencing trashed items, etc. leading me to believe the **dd** failed to have the desired effect.

---

### Post by linkageless on 2011-06-03
Yes, it absolutely failed if you can see files. If you dd if=/dev/zero of=/dev/sdb-or-whatever-it-is and you still see something when you fdisk -l /dev/sdb-or-whatever-it-is then there's no writing going on at all.

I'm wondering if there is a proprietary way of making this device read-only or if something has failed as with my sdhc card reader. Perhaps someone with more in-depth usb mass storage experience might comment.

---

### Post by robbiemacg on 2011-06-03
I'm inclined to agree with you. There's definitely something unusual going on.
A couple of experiments at work today on machines running XP were similarly unsuccessful, yielding warnings/errors that talked about 'write protection'. Same result as on my Linux systems, I couldn't force the formatting.
At this point, I might well approach the shop where I got the thing looking for an exchange. (Big box store, so I'm not sweating their margins.)

---

### Post by linuxinstalledfromhdd on 2011-06-03
Return it and get a good brand name version. Not the cheapy ones. :)

---

### Post by robbiemacg on 2011-06-03
LULZ. I feel a real sense of disappointment when I can't fix my own tools, but I'm increasingly friendly to that suggestion, [linuxinstalledfromhdd]("http://ubuntuforums.org/member.php?u=1050936"). Right now I feel like fixing this drive with a hammer.

All right, thanks gang. I'm decommissioning this thread, taking a spin my the big box store (and the friendly brewery next door). Your suggestions were sound, as always.

---

### Post by linuxinstalledfromhdd on 2011-06-03
I got a whole bunch of them once on Ebay from China for next to nothing. All of them lasted about 40 days time. And today they are now things I use to scrap bird stuff off my car when I take it to the car wash. They work really good at that. I tell the guys at the wash it's my new invention. lol

---

### Post by robbiemacg on 2011-06-03
That cheers me significantly. Thanks for sharing that one, chum. HA.

---

