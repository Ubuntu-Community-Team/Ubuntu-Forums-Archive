---
title: "Sector failure on primary partition"
date: 2010-10-26
forum: General Help
---

### Post by john77eipe on 2010-10-26
Hi all,

I have a dual bootable Win7 and ubuntu 10.4.

Something went wrong with my HardDisk and it's on my primary partition where windows is installed. So, windows no longer loads but the partition where Ubuntu is installed works so I'm able to boot in. Through ubuntu I access my NTFS drives. 
Certain files in that affected partition doesn't work. Not able to both read and write. 

Do I need to replace my HD? Is it possible to install windows on that drive again automatically skipping the affected sectors.

---

### Post by john77eipe on 2010-10-26
Anyone out there who could help? I'm totally new to this. :(

I have attached the screenshot of SMART Data check. (It went to 90% and then froze)

---

### Post by s.fox on 2010-10-27
Thread Moved to  [General Help]("http://ubuntuforums.org/forumdisplay.php?f=331") at op request.

---

### Post by srs5694 on 2010-10-27
Yes, replace the hard disk. Do it ASAP. I recommend shutting down the computer and not turning it on (even in Linux) until you've got the replacement drive installed and ready to transfer data.

There are many ways to copy the data. You may need to resort to a fault-tolerant tool like ddrescue to copy the Windows partition; or you could re-install Windows from scratch and then copy any user data files you might need.

---

### Post by john77eipe on 2010-10-27
so I have to replace HD. That's sad. 
I thought I could live with it for another few months as I have 4 NTFS partitions and 1 ext4. And only 1 of the NTFS partition is facing error.

Not worried about windows (I have also taken backup of important files) but is there a change that the sector failures will increase dramatically?

---

### Post by srs5694 on 2010-10-27
> **john77eipe said:**
> is there a change that the sector failures will increase dramatically?

***YES!!!***

I wrote "do it ASAP," and I *meant it!*

Hard disks fail for a variety of reasons. It's unclear why yours is failing. Some causes result in rapid deterioration as the drive is used. For instance, there could be a bit of dust inside the drive bouncing around. Every time it hits a platter, that degrades it, perhaps wiping out a sector or two. It's like the old Breakout game; when the ball (the bit of dust) gets behind the wall, the wall breaks down pretty quickly.

OTOH, the drive could be failing in some other way that will remain localized to those sectors that have already failed, or spread slowly to nearby sectors. The point is that neither you nor I know how it's failing -- just that the process has already started. If you value your data, transfer it to another drive *now.* Go to Best Buy, Staples, or wherever, and get a new disk *today.* Don't buy it online and wait a week for it to be delivered; Murphy is watching, and if you do that, his Law will come into effect and you'll lose all the data the day after you place the order.

---

### Post by john77eipe on 2010-10-27
Done.. I'm replacing it tomorrow.

Thanks for your advice. I had already taken backup of all important files.

---

