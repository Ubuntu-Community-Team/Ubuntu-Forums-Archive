---
title: "Partition name question"
date: 2010-01-26
forum: General Help
---

### Post by Al Fischer on 2010-01-26
I had 3 primary partitions on a drive. SDB1, SDB2, SDB3. I deleted SDB1 using GPARTED. Now I have 2 partiions. SDB2 and ADB3.
How can I cause them to be SDB1 and SDB2?

I was doing this because when installing Win 7 it created a hidden 'system reserved' pafrtition which I did not want. I am trying to do multiboot with Ubuntu, Win7, XP, and DOS.

I gues what I do not understand(among many things!) is what causes them to be SDBx.

---

### Post by warfacegod on 2010-01-26
sdb is the "marking" system Linux uses for hard drives like Windows uses c: d: e:

Examples:

sda1 is the first drive, first partition

sda2 is first drive, second partition

sdb4 is second drive, fourth partition

sdc3 is third drive, third partition

---

### Post by Al Fischer on 2010-01-26
Yes, I understand that. I deleted SDB1 in an attempt to straighten out a Wundows 7 install problem Now the first partition shows as SDB2, I want to make it show as SBD1.

---

### Post by warfacegod on 2010-01-26
Why?:confused:

---

### Post by garvinrick4 on 2010-01-27
> **Al Fischer said:**
> I had 3 primary partitions on a drive. SDB1, SDB2, SDB3. I deleted SDB1 using GPARTED. Now I have 2 partiions. SDB2 and ADB3.
How can I cause them to be SDB1 and SDB2?

I was doing this because when installing Win 7 it created a hidden 'system reserved' pafrtition which I did not want. I am trying to do multiboot with Ubuntu, Win7, XP, and DOS.

I gues what I do not understand(among many things!) is what causes them to be SDBx.
You only got 4 primarys. One is system for boot one is for 7 OS one is 7 recovery one is
XP gotta get rid of something for extended for Linux logicals. Make sure you have made your windows 7 disks 3 DVDs if you are gonna get rid of Recovery partition. Windows will only reside in 1,2,3 or 4 and one of them has to be linux extended partition.  Google gparted the software for ubuntu partition tables and get instructions to do what ever you want with your table.

---

### Post by Al Fischer on 2010-01-27
Well, after a good nights sleep and a pot of coffee, I managed to figure out what I needed to do. First, Win 7 had taken a primary partition for 'system reserved' which I do not need as I will not be using Bitlocker. So I had deleted it and thats where this started. 
I want the following partitions:

Win 7
XP
Ununtu
Dos (where Grub for DOS will reside)

Total 4 primarys.
(doing this with now with 3 for XP, Ubuntu, DOS) Works great.

How I fixed this mess.
1. GPARTED copy partition to another drive. (I'm paranoid!) 
2. Booted it. Of course the partition table was invalid so Win 7 doesn't boot. Put in the Win 7 DVD and let it have at it for about an hour doing a 'repair'.
3. Booted Win 7 fine.
4. Cloned drive back to the priginal drive with Acronis TI 2010.
5. GPARTED set partition to the size I wanted.
6. Now the partition shows as SDB1 with 100 gig like I wanted.

This all started because WIN 7 took a primary partition that I wanted to use. UBUNTO SCORES AGAIN!!

---

### Post by Al Fischer on 2010-01-27
GARVINRICK4: What do you mean by the Win 7 3 DVDs?

---

### Post by warfacegod on 2010-01-27
7 doesn't like having "other" OS's installed next to it (or in the same town for that matter). You may need to use the discs to fix the Wiindows MBR. The other scenario is: by removing the recovery partition, the only remaining option is the Windows install discs for when (not if) Windows ahs a catastrophic failure.

---

### Post by Al Fischer on 2010-01-27
But what 3 DVDs are you referring to? How do I create them?

I have the originsl WIN 7 Professional dvd. That's what I used to fix the MBR.

---

### Post by warfacegod on 2010-01-27
> **Al Fischer said:**
> But what 3 DVDs are you referring to? How do I create them?

I have the originsl WIN 7 Professional dvd. That's what I used to fix the MBR.

Then that should do fine. Having never used 7, wasn't exactly sure what 3 discs garvinrick4 was referring to but I didn't want to leave you in the dark so I gave you what I was 99% sure was the correct answer.

---

### Post by Al Fischer on 2010-01-27
Thanks for the replies. I am aware of the problems of more than 1OS and have had catastrophic failures and had to reload. Most were probably my fault as I think I caused it with Partition Magic. I ended up with 2 drives in the machine with active partitions and XP did in both images. I have found that once I get the unneeded OS hidden I have no problems. If MS ever gets into Linux then things MAY change. But I doubt it. Setting up Win 7 has been a real learning experience and I am not ready to give up good old XP or Ubuntu and sometimes DOS is the only solution. 

So far I have all four working multiboot and will do a full backup for when it blows up (not if, when!!)

---

### Post by garvinrick4 on 2010-01-28
> **Al Fischer said:**
> GARVINRICK4: What do you mean by the Win 7 3 DVDs?
When you get your Machine installed with windows 7 it has a 12 gigabyte image to make 
and lets you copy to 3 DVD's so you have install disks. You get to do this 1 time only, make the
3 DVD's. Also lets you make recovery disk, takes one DVD. Those you can make all you want.
 I am in Ubuntu right now so I cannot give you file name in Windows 7 but it is in APP's. Will look next time in Windows to update and post here.

---

