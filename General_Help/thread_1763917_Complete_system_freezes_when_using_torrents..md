---
title: "Complete system freezes when using torrents."
date: 2011-05-21
forum: General Help
---

### Post by xyvian on 2011-05-21
Beginning on the release day for Firefox 4, my system has been encountering hard freezes (no responsiveness to any key entry and only way to restart is by hitting the reset button). I had installed firefox 4 with no issue, but once it was open, it kept freezing my system. Some addons weren't supported anyways, so I uninstalled it and got back my 3.6. At the time I was using rtorrent, but within minutes of using it since the firefox install, my entire system freezes up.

Naturally I suspect HDD or RAM, but both have been extensively tested. Next I began browsing forums and found some tricks like turning off IPv6 or changing settings via HDPARM, but none have made any difference. I have moved on to using Transmission, and the problem still exists, but it occurs much less frequently.

I have also since then noticed that transfers of files from my 500GB OS/Torrent drive to my RAID 5 array and vice versa moves at 2-4MBytes/s, much too slow. So next I set up my torrent client to download directly to my RAID array, and lo and behold no freezes! Also, while transfering data the system moves at an absolute CRAWL, as in browser windows turning gray, saying that they have stopped responding, etc.

I ran a fsck on my 500GB drive, which instantly told me my file system was clean.

I'm at my whit's end here! I hate re-posting on a topic, but I feel like I've tried everything!

System Info:
Ubuntu 10.04 32-bit
Kernel 2.6.32-29-generic-pae
AMD Athlon 4450e 
1GB RAM, 2.5GB Swap
Gigabyte GA-MA74GM-S2 Motherboard
Nvidia GeForce 210 - driver version 256.53
1 500GB WD5000AAKS formatted ext3
3 750GB WD7500AACS (greens) in a RAID 5 formatted xfs
Gigabit NIC, not wireless
NO CD Drive- I use my flash drive



HELP!

---

### Post by prshah on 2011-05-21
> **xyvian said:**
> 
I ran a fsck on my 500GB drive, which instantly told me my file system was clean.

I really think it is file system related. Running an fsck on a mounted filesystem will simply report whether or not the file system is "dirty" (Eg not cleanly shutdown). To run a proper file system check, place a file "forcefsck" in the root of the file system, and reboot. Eg```
sudo touch /forcefsck
```
After the reboot, the filesystem will be checked throughly.

Hope this helps.

---

### Post by inameiname on 2011-05-21
I've been having freezing issues ever since installing Natty. May or may not be your issue, but I'll link you to a post about it anyway:

[http://ubuntuforums.org/showthread.php?t=1749511](http://ubuntuforums.org/showthread.php?t=1749511)


I do not really think your issue is torrent-related, but who knows. Personally, when using Transmission, I do notice my computer running much slowing, particularly the Internet. This always happens to me, even way back with Jaunty, my first Ubuntu experience. Again, may or may not similar to your trouble, but worth mentioning.

---

### Post by xyvian on 2011-05-21
> **prshah said:**
> I really think it is file system related. Running an fsck on a mounted filesystem will simply report whether or not the file system is "dirty" (Eg not cleanly shutdown).

I had run the fsck from a bootable Ubuntu from USB, but I will try this method anyways.

---

### Post by xyvian on 2011-05-21
> **inameiname said:**
> I've been having freezing issues ever since installing Natty. May or may not be your issue, but I'll link you to a post about it anyway:

[http://ubuntuforums.org/showthread.php?t=1749511](http://ubuntuforums.org/showthread.php?t=1749511)


I do not really think your issue is torrent-related, but who knows.

Thanks for the link and input, however when my system freezes, no key combinations work - thus the 'Hard Freeze' I'm referencing. And no, I don't blame torrents for freezing my system, it's probably the massive throughput of data that's freezing the system.

Xyvian

---

### Post by xyvian on 2011-05-21
Alright, I ran the fsck as prshah suggested. It ran for 10-15 minutes, during which I had left the room and when I had come back the system had completely booted. I tested rtorrent out, and again it caused my system to freeze. I did realize something, though. When I am torrenting on my OS drive, the HDD light is constantly on, while when I am torrenting on my RAID array, the light only blinks every once in a while.

Is there a log report located somewhere that will tell me the results of the fsck so that I can post it? Are there any other logs that would be helpful to post so that I can get my problem resolved?

Thanks a bunch,
Xyvian

---

### Post by inameiname on 2011-05-21
Ah. Sorry you are still getting the problem.


As for my issues with the computer freezing, nothing would unfreeze it as well. No key combination, nothing. The only thing that has drastically limited the occurance of this issue for me is to log in as Ubuntu Classic (No Effects). Not a permanent solution, but it seems to help. Perhaps test it on yours to see if it helps/hurts/does nothing.

---

### Post by prshah on 2011-05-21
> **xyvian said:**
> the HDD light is constantly on,

Is there a log report located somewhere that will tell me the results of the fsck so that I can post it? Are there any other logs that would be helpful to post so that I can get my problem resolved?

From your description, I suspect bad sectors.

If this is true, you should find a bunch of errors in the dmesg log; try ```
cat /var/log/messages|grep -i drdy
``` (DRDY errors are common when the filesystem is affected).

You can run a more detailed check on the (unmounted) filesystem by booting off a live CD and using the badblocks program (checking only) or fsck -c (check and mark unusable).

Please post back if you need more information.

---

### Post by xyvian on 2011-05-22
> **inameiname said:**
> Ah. Sorry you are still getting the problem.


As for my issues with the computer freezing, nothing would unfreeze it as well. No key combination, nothing. The only thing that has drastically limited the occurance of this issue for me is to log in as Ubuntu Classic (No Effects). Not a permanent solution, but it seems to help. Perhaps test it on yours to see if it helps/hurts/does nothing.

My system is on Ubuntu Classic, so it's not that.

---

### Post by xyvian on 2011-05-22
> **prshah said:**
> From your description, I suspect bad sectors.

If this is true, you should find a bunch of errors in the dmesg log; try ```
cat /var/log/messages|grep -i drdy
``` (DRDY errors are common when the filesystem is affected).

You can run a more detailed check on the (unmounted) filesystem by booting off a live CD and using the badblocks program (checking only) or fsck -c (check and mark unusable).

Please post back if you need more information.

Unfortunately using the code you posted outputs no data ie ```
bwm@nas1:~$ cat /var/log/messages|grep -i drdy
bwm@nas1:~$
```

I have run extensive HDD tests on the drive, however. Both the Western Digital quick and long tests pass, as well as a full surface scan from HDAT2. The SMART status is also good. I will go ahead and run a badblocks on it over night.

More in the morning.
Xyvian

---

### Post by prshah on 2011-05-22
> **xyvian said:**
> Unfortunately using the code you posted outputs no data ie ```
bwm@nas1:~$ cat /var/log/messages|grep -i drdy
bwm@nas1:~$
```

I have run extensive HDD tests on the drive, however. Both the Western Digital quick and long tests pass, as well as a full surface scan from HDAT2. The SMART status is also good. I will go ahead and run a badblocks on it over night.

Considering all this, I don't think bad sectors are the problem. Maybe you need to look at something else, but I have no idea what else.

Good luck in your quest.

---

### Post by xyvian on 2011-05-22
Badblocks has been running for six hours and has only gotten 5% through the first testing pattern. I'm used to badblocks taking a long time, but I've never had it go this slow. At this rate, it will take 20 days! I will restart badblocks from a Knoppix CD, since the Ubuntu CD I had to use the -f flag, perhaps that is why it is taking so long.

I'll post more info as it becomes available.

I'm thinking I may have to partition my HDD's data away and reinstall Ubuntu,though. I'm really trying to avoid that, though, as I have this system set up just how I want it.

Thanks for everything,
Xyvian

---

### Post by xyvian on 2011-05-24
So I have repartitioned my HDD so I could install 11.04. I gave it its own 90GB partition, and installed it. I felt that the install took longer than necessary, but I was patient with it. Once it finished, I immediately tested with a torrent, and I experienced the same slowdown and freezing I have had before. This leads me to believe that my issue is HDD related, even though my extensive testing has told me otherwise. I will be opening an Advanced RMA with Western Digital so I can back up all of my data.

As an afterthought, I find Unity to be a bit clunky and counter-intuitive in places...

Thanks for all of your help & I will post when I get my HDD set up,
Xyvian

---

### Post by linuxinstalledfromhdd on 2011-05-24
Did you run Disc Utility on it to see what says?  If it says good, then you keep trying. Anything less and I would replace it.

---

### Post by xyvian on 2011-05-24
> **linuxinstalledfromhdd said:**
> Did you run Disc Utility on it to see what says?  If it says good, then you keep trying. Anything less and I would replace it.

Yes, I have run Disc Utility, and yes, it says it is good. I have also run the Western Digital testing software, and it has passed both the short and the long scans. I have also personally looked over the SMART status of the drive (which is impeccable) as well as done a full surface scan of the HDD with a third party software (HDAT2 found on the Hiren's Boot CD).

I have run a fsck scan on the primary ext3 partition of Ubuntu 10.04 which passed w/o error. I have run memtest for extended times, getting no errors. The motherboard has no bad capacitors. Ubuntu runs extremely fast, without issue when run off of a USB flash drive. I have no error messages in my /var/log/messages. 

If you can think of anything new, please let me know!

Xyvian

---

### Post by xyvian on 2011-05-25
Alright, so I still have not started the RMA process on my drive. I am just loath to spend the money to ship it back if that's not the issue. I took a screenshot of my system doing a file copy from one location on the 'faulty' HDD to another on the same drive. As you can see, the top report shows that CPU activity is very low, however the iotop terminal shows IO> as being very high, typically 99.99% for both processes while those processes actually have very little read/write speed. They will flash with speeds up to 2-3MB/s. The mpstat window shows a gradual increase in %iowait, where the higher the %iowait, the worse the computer's performance gets, until such a point that each mpstat command takes minutes to output its data, and browsing the net or even opening folders on the computer takes so long, the file transfer will often finish before the system responds to user interaction.

I have done some googling around and I have found that in top, a high %wa value is indicative of some kind of IO fault, as it shows how much of the CPU is waiting on an IO command.

This data has all been pulled off of my 11.04 install I just did, as somehow when I resized the partition 10.04 was installed on, I broke the install and it no longer boots :frown:

If anyone can make sense of this, please let me know!
Thanks again,
Xyvian

---

### Post by xyvian on 2011-05-26
Ok, so I am glad I took today to work on this problem, because I have finally solved it. Guess what? It was the HDD all along!!!

Boy was that drive refusing to tell me it was failing. What I finally did was take the HDD out of my Ubuntu box and throw it into my Windows gaming rig, and booted it up. I had the same old experience I was having before. I checked the SMART status while it was in this computer, and what do I find? 28 Ultra DMA CRC Errors! Finally some news and some closure!

I went to RMA the HDD with Western Digital, but unfortunately it was about a year out of warranty, so I'm out of luck getting a free replacement. I have since then installed a temporary Ubuntu on an old 60GB Hitachi 'Deathstar' until such a point in the future that I can purchase myself a new HDD.

Thank you all for all of your help and your input. I hope this helps someone else in the future.
Xyvian

---

