---
title: "Best file system for an external hard drive"
date: 2010-08-22
forum: General Help
---

### Post by altonbr on 2010-08-22
I have a 1.5TB Western Digital Caviar Green in a USB 2.0 external setup with an ext4 file system.

I'm going to purchase a 2.0TB Western Digital Caviar Green in a USB 2.0 external case, copy the data over and put my 1.5TB in a fire-resistant box in another house.

I'm worried about a couple things however:

(1) I'm worried about the long-term viability of _any_ file system years into the future. I've been storing my data on hard drives (instead of CDs, DVDs or BDs) for years now due to their higher reliability than optical disks. However, the file system used in optical disks is [UDF]("http://en.wikipedia.org/wiki/Universal_Disk_Format") which I think has much longer viability into the future. I'm not going to store terabytes of data on optical discs of course, so I'm wondering what I should choose for a hard drive file system. FAT32 or NTFS (due to Windows' 90%+ presence on the desktop, including still being used by Windows 7) may be the best choice, but I much rather have a open source file system, especially one that allows for permissions, timestamps, etc.

(2) As for my 2TB hard drive that I will be using for a while into the future, should I continue to use ext4 (I've had no problem with it thus far), but is there another file system that has better performance when storing and transferring gigs of data?

Interested in your thoughts.

---

### Post by john newbuntu on 2010-08-22
1. You may already know this and answered it.  NTFS over FAT32 (FAT32 has about 4GB file limit plus other problems).  You could compress/image directories/files from other OS and store it on NTFS to preserve permissions and timestamps. Should you desire to store it at a file level, you will require a native(ext4)  filesystem.

2. I think btrfs, NILFS and reiser4 will be thrown in by others.  But here are some benchmarks between ext3,4 and btrfs.  I admit I am not into mission critical, high performances apps.  I feel ext4 does its job well having had it since Karmic.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_netbook_fs&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_netbook_fs&num=1)

Part of your performance bottleneck will be from the USB2.0.  Perhaps e-sata or USB3.0 would have been be better options.  Also, do run fsck/chkdsk on both your drives periodically.

---

### Post by Ginsu543 on 2010-08-22
You make it sound like you're putting this backup drive into a time capsule and not a safe box. If all else fails and the file system you used becomes totally obsolete, you can just copy the data over to another drive in a format that is more current and put that in a safe box. I really don't think it matters too much what file system you use for a drive you're using for backup storage (you don't even really need a high-performance file system because you won't be reading/writing to it regularly).

I would save the data in NTFS format for best compatibility, but ext4 would be fine, too, I think. Even if ext5 were to ever come out, Ubuntu would still maintain backward compatibility with ext4, just as it maintains backward compatibility with ext3 right now.

---

### Post by spibou on 2010-08-22
> **altonbr said:**
> I have a 1.5TB Western Digital Caviar Green in a USB 2.0 external setup with an ext4 file system.

I'm going to purchase a 2.0TB Western Digital Caviar Green in a USB 2.0 external case, copy the data over and put my 1.5TB in a fire-resistant box in another house.

I'm worried about a couple things however:

(1) I'm worried about the long-term viability of _any_ file system years into the future.
That's an intriguing question. I should have thought of it myself since I also store data for long term access. The first thing is how long-term are we talking about ? Decades into the future ? Do you want your grand-grandchildren to have access to the data ?

I would say go for UDF. Your own link says that UDF is storage medium agnostic so there's nothing preventing you from turning your filesystem into UDF format and storing it in whatever medium suits you best. I wouldn't exclude DVDs. It wouldn't take a huge amount of DVDs to store 1.5TB of data. Are you sure that hard disks are more reliable than DVDs ? I was under the impression it's the other way around. For one thing a DVD is independent of the device you use to read or write to it which is not true for hard disks (unless you have access to very expensive equipment , I think). And , speaking just out of vague intuition , isn't there a danger that the ferromagnetic material on the hard disk may be demagnetised over time or something ?

I can certainly imagine that decades into the future you will be able to go into a computer store and buy a DVD reader which will come bundled with software and which will allow you to read your DVDs in whatever computer hardware and operating systems have become established at such a time. It's much like these days you can still buy floppy disk drives although hardly anyone uses them to store new information. But I think it's a lot less likely that you will be able to connect the hard disks of today with the computers of the future.

Another advantage of UDF , independent of storage medium , is that it is an open format so manufacturers of hardware and software who will want to support it will likely not have any legal obstacles. The fact that UDF is not connected to any specific operating system also makes it more likely that it will continue to be supported a long time into the future.

Having said all that , if you want to play it 100% safe then your best strategy is to update your storage medium every 5 years or so. So today it may be a hard disk , in 5 years a new technology , in 10 years yet another one and so on. It seems likely that no technology , hardware or software , will become totally obsolete within any 5 years long period so you won't have trouble making the transfers from the old medium to the new one. Apart from that , if your data is really valuable to you then you want  to have it stored in more than one places anyway.
> 
I've been storing my data on hard drives (instead of CDs, DVDs or BDs) for years now due to their higher reliability than optical disks. However, the file system used in optical disks is [UDF]("http://en.wikipedia.org/wiki/Universal_Disk_Format") which I think has much longer viability into the future.
I agree for the reasons mentioned above. I imagine also that a lot of people store their data on DVDs for long term preservation which makes it more likely that both the medium and the format will continue to be supported in the future.
> I'm not going to store terabytes of data on optical discs of course, so I'm wondering what I should choose for a hard drive file system. FAT32 or NTFS (due to Windows' 90%+ presence on the desktop, including still being used by Windows 7) may be the best choice, but I much rather have a open source file system, especially one that allows for permissions, timestamps, etc.Even if the filesystem does not natively support permissions , timestamps and similar you can make a huge tar file of your data which will have all that information. If the storage filesystem can accommodate a file that big then it will work although it won't be very convenient.

Have you looked at all into magnetic tapes ?

---

### Post by hugo87 on 2011-01-19
I realize this thread IS a bit old.

However, there's something you haven't considered.
By the time ext3, ot whatever you choose becomes obsolete, and unusable, SATA2 or USB will be gone as well.
Consider you can still mount ext2 or FAT16 drives, but the IDE connector from 15 years ago, might give you a much harder time.

---

### Post by momoxxen on 2011-01-20
i have a 2TB external HD also that i want to format. for now im just using NTFS as default format. but i notice its a bit slow when handling such a large files and folders. 

FYI i got 20gb of music, around 5gb of photo. 500gb of videos and almost 100gb of ISO.

i'm looking for a reliable, fast and stabil format for my external HD. can u help out?

---

### Post by yetiman64 on 2011-01-20
> **momoxxen said:**
> i have a 2TB external HD also that i want to format. for now im just using NTFS as default format. but i notice its a bit slow when handling such a large files and folders. 

FYI i got 20gb of music, around 5gb of photo. 500gb of videos and almost 100gb of ISO.

i'm looking for a reliable, fast and stabil format for my external HD. can u help out?

I've been using ext4 in Lucid to manage a similar amount of data as yours in 300 000 + files, on both  eSATA and USB 2.0 drives. Ext4 is performing nicely for me.

---

### Post by tredegar on 2011-01-20
Bear in mind that for or long-term storage, you will need to keep updating your storage hardware.

Some thoughts:

How many people now have the technology to play 78RPM records (an ancient monaural audio format, no electricity required, just "clockwork")? Or reel-to-reel 1/4" tape? Or an "LP"?

I still have some paper-tape and punch-card records. No reader now. But I expect I could make one easily enough, the technology was _very_ simple..

Could you read an 8" floppy, or a 5 1/4" floppy, or even a 3 1/2 inch one now?

Clay tablets are readable after many thousands of years (if anyone then understands the language), but they are slow to write, difficult to transport and bulky.

Somewhere in the attic I have 4K of 16-bit core memory, with a TTL interface. It will still faithfully be remembering the last program I ran on it all those years ago, and technically will still be readable in ten thousand years (probably all the cores would have to be rewired first), but that stuff is bulky and not widely available now.

I have some photographs dating to the 1860's. They are perfectly viewable, if brittle. I doubt my digital photographs, even if printed with today's ink on today's paper, will last 150y.

The bottom line: You'll have to keep switching formats every 5-10y. It's what keeps business in business.

Good luck with your archives.

---

### Post by spibou on 2011-01-20
> **tredegar said:**
> 
I have some photographs dating to the 1860's. They are perfectly viewable, if brittle. I doubt my digital photographs, even if printed with today's ink on today's paper, will last 150y.
I don't see why not.

---

### Post by tredegar on 2011-01-20
> I don't see why not.
Modern pictures are printed with dyes. Old photographs were made with silver ( **Ag** in the periodic table ).
Dyes fade, silver doesn't, but silver photographs are only greyscale (excellent resolution though).

Please try printing a picture twice, put one by a window, in sunlight, and the other in a plastic bag in the freezer. Compare them a year later. You will be suprised by the difference. Now extrapolate 20 or 150 years. You will realise that the information / image / data will soon be lost.

---

