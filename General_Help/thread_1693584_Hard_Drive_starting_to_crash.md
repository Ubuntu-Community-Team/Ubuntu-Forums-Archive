---
title: "Hard Drive starting to crash"
date: 2011-02-23
forum: General Help
---

### Post by manners2345 on 2011-02-23
I think my Hard Drive is starting to fail. It is 1.5 years old.

 It is 500GB

I seem to remember in the days before Windows there was DOS which had some pretty Good UTILS. One of them being a Util that would check your hard drive, and lock out bad sectors. would not stop till it had done the WHOLE hard drive, even had a funky GUI with it,in Windows 95

I have tried to use the SMART STUFF associated with the hard drive. It runs the BASIC SELF TEST, says hard drive is healthy.If I try to run the extended test it fails after about 2 minutes. Last week I had 26 bad sectors, this week I have 55. now I get READ ERROR when I try to start up.

I have figured out how to make a system rescue disk from source Forge an put it on a USB 4GB stick.There do not seem to be any useful UTILS on to solve my problem.

I I load TESTDISK to this system, it is owned by ROOT which makes it WORTHLESS!!

I am the only person who can log on to this computer

I still have a Windows 98 cd which I think still has DOS 6.22 on it. 

How would I make a boot-able USB stick with DOS

Any suggestions

THAN YOU in advance for any help!!!!

---

### Post by howefield on 2011-02-23
Moved to "*General Help*" where you are likely to get better help for your query than you would in Tutorials & Tips.

---

### Post by manners2345 on 2011-02-23
Thank You

---

### Post by PratterFak on 2011-02-23
One thing I just want to throw out there- could you have a failing power supply? It may seem weird, but I would question that too in your trouble shooting. Lack of, or dirty power can cause other hardware failures.

You happen to have another PC you could access the drive with?

---

### Post by 3rdalbum on 2011-02-23
In the days of DOS 6 you needed that sort of stuff. These days however, disks will automatically identify bad blocks, copy their contents to a new spare block if possible, and then flag the bad block.

If you are getting read errors and your drive is developing 20 bad sectors a week, then back up ALL your data NOW and replace the disk. It is failing and it will take your data with it. You cannot save the disk.

---

### Post by mciverza on 2011-02-23
"testdisk"  and "fsck" can help you with that. I strongly recommend booting from a liveCD and then running fsck

if you have ext4 filesystem, then you'd need to run something like the following in a terminal.
sudo fsck.ext4 -c -f -p -v /dev/sda1
... you'd need to replace /dev/sda1 with the actual disk and partition you're wanting to check

---

### Post by manners2345 on 2011-02-23
One thing I have noticed is that as the capacity of hard drives increase the life span decreases. On this laptop I have a 10 GB, it has lasted over 4 years now. When hard drives were less than 1GB a system that had over 80 computers setup,they all had 512MB or less we averaged less than 1 hard drive every 3 years, going 10 toes up.

This is the second hard drive of over 300GB start dieing with less than 2 years use.

POWER: from the wall,220 Volts, it is hooked up to an APC UPS, 220 out, then into a votage regulator 110 Volts out, then into a SURGE PROTECTOR STRIP, then to the equptment.

---

