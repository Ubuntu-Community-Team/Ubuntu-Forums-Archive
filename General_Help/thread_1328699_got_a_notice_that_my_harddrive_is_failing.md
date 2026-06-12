---
title: "got a notice that my harddrive is failing?"
date: 2009-11-16
forum: General Help
---

### Post by eulnuj on 2009-11-16
so after i install 9.10 the first pop up message i got was that my harddrive may be failling, but i don't notice anything wrong. i remember a while back i install fedora and i got same message but since then nothing happen.

should i worry about it?

---

### Post by kirmonkey on 2009-11-16
I wouldn't worry about it.

I would keep a regular backup of /home and /etc to another HDD though!

There are those who backup and there are those who have never lost data!

I use back-in-time to backup to a separate "My Book" HDD.

---

### Post by MatthewMetzger on 2009-11-16
I wouldn't worry about it, but I agree with kirmonkey. Have an automated backup. If you have the money, buy a new Seagate drive and use CloneZilla to clone the old drive to the new one. Better safe than sorry.

---

### Post by dasunst3r on 2009-11-16
If you are interested in what's triggering this warning, you could go to System -> Administration -> Disk Utility.  Attached is mine (with the disk's serial number blurred out).  Please come back with what the utility claims to be failing, and then we should be able to provide you with a better picture of what is going on.

---

### Post by eulnuj on 2009-11-18
[IMG]http://tinypic.com/?t=postupload[/IMG]> **dasunst3r said:**
> If you are interested in what's triggering this warning, you could go to System -> Administration -> Disk Utility.  Attached is mine (with the disk's serial number blurred out).  Please come back with what the utility claims to be failing, and then we should be able to provide you with a better picture of what is going on.

The rest are find.

---

### Post by kirmonkey on 2009-11-18
From the screenshots it looks like there are "bad blocks/sectors" on the HDD - blocks/sectors that are physically damaged. The disk/OS has marked these blocks/sectors as bad and moved the data to another place on the disk. It then marks the blocks/sectors as "bad" so they are never used again.

Get your notebook (paper one) out and jot down how many bad blocks/sectors there are and see if this number increases over time. If it does then you may need to take further action.

It may be worth searching for "bad sectors/blocks" on the net and also search and read about S.M.A.R.T - a system that HDD manufacturers put on disks to detect this fault. I don't know enough to advise here.

---

### Post by WatTwo on 2009-11-18
I got the same thing, said i have bad sectors.

---

### Post by dcstar on 2009-11-18
> **WatTwo said:**
> I got the same thing, said i have bad sectors.

Then get a replacement hard disk before this one dies and you lose data - you have been warned.

---

### Post by WatTwo on 2009-11-18
Yeah, but it never showed it windows... then again, windows is....yeah

I have most of my things backed up already :)

---

### Post by whoop on 2009-11-18
> **dcstar said:**
> Then get a replacement hard disk before this one dies and you lose data - you have been warned.

I agree, as soon as I get stuff like this I replace the disk immediately. 
I don't worry, because I do this.

---

### Post by whoop on 2009-11-18
> **WatTwo said:**
> Yeah, but it never showed it windows... then again, windows is....yeah

I have most of my things backed up already :)

Do you have hard disk monitoring software installed in windows? Maybe the partition containing windows hasn't corrupted (yet).

---

### Post by blueridgedog on 2009-11-18
85 sectors is a bit high to gamble with.  A drive is always easy to replace when YOU want to.

---

### Post by WatTwo on 2009-11-18
I did a wubi install, so its on the same partition. i need a bigger hhd anyway.

---

### Post by jerrylamos on 2009-11-18
It did fail.  After a while.  

Oops, I better save my files on a USB drive.  Did that.

I had quad boot installed, four images.  First one went sour, then another.  Intrepid 8.10, Jaunty 9.04, and two Karmics 9.10.

So I ordered a hard drive, installed a karmic, then copied over my files which I had 4 copies two unreachable by then.

Impression I got was the drive itself was reporting it was sick.  It is.

Thanks, Ubuntu.....

Jerry

---

### Post by blueridgedog on 2009-11-18
Palimpsest is a great tool.  Odd that it is standard now, but you have to install gparted if you want it.

---

### Post by fluffman86 on 2009-11-18
Meh, I got SMART errors on two separate disks two years ago.  I'm still using the disks.  

SMART is just reading the info provided by the disk *manufacturer*.  That's right, the people who *sold* you the disk are giving you an error that says you should buy a new one.  

Am I the only one that finds that to be a little fishy?  I mean, the error *could* be true.  And your drive *could* die soon.  But is soon a year from now? Two years? 

The point is that you should keep backups *all the time*...not just when you think there might be a problem.  You never know when your house will catch on fire, or someone will steal your stuff, or even if your hdd will randomly just *DIE*.  So keep a spare of all of your data off-site somewhere--either with a relative or in a safe deposit box at the bank.

---

### Post by dasunst3r on 2009-11-18
I replaced the Western Digital hard disk that came with my Dell not long ago with a Western Digital 320GB, 7200RPM Scorpio Black for $82 or so.  Here's how you do it:
[list=1]
[*]Go to [www.wdc.com](www.wdc.com)
[*]Go to Support -> Warranty & RMA Services
[*]Click on "End User Customers"
[*]Click on "Warranty Check"
[*]Enter the serial number on your hard disk.  You should see that there's no warranty, but it should offer you a loyalty discount on a new drive.
[/list]
Actually, you can do this with any Western Digital hard disk.  Basically, you will be "trading in" the remaining warranty (if any) on the existing hard disk in exchange for a discount on a new drive.  They'll ship you a new, bare drive (i.e. no retail packaging, no cables, etc.), and you don't have to ship your old drive back to them.

---

### Post by User3k on 2009-11-28
I am more then a little annoyed at this myself. I have 3 sata's and one IDE. According to Palimpsest they are all failing. How interesting.

So I might believe one or even two at the most could be failing due to some serious bad luck, but all four of them at once? I don't think so.

I checked each with the manufactures testing tools, WD and Seagate, and all is fine with them. I would really love to have a tool like this that actually worked and did not return false positives. 

So for now I just turned it off until I am sure that they got this working right. All these people online having that many hard disk failures, and some with brand new drives, is enough to get a person thinking. But for me having four drives at once is proof enough that something is wrong with Palimpsest.

With that said, it is ALWAYS a good idea to keep all your data backed up no matter if your hard drives are new, old or whatever.

---

