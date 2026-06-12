---
title: "Is a SSD a mistake?"
date: 2012-03-21
forum: General Help
---

### Post by bertmanphx on 2012-03-21
Hello,
I'm needing to update my wife's computer here, and purchased a decent ( I think ) solid state drive, hoping to pick up some efficiency.   However, I keep finding horror stories about their short life span.  Should I take this thing back before I open it?  Bottom line, if I get a year or two out of it, I'll be happy.
Any input is appreciated.

Thanks,

bertmanphx

---

### Post by ksa618 on 2012-03-21
As I've understood it, the mean time between failure is approximately the same for SSD's as traditional hard drives. If you're worried, and there's plenty of RAM on the computer, just don't put a swap partition on the SSD. I have some experience with running Ubuntu on a compact flash, and it will run for years without swap, but with swap, the flash dies quickly. But then, compact flash is nowhere near SSD's in reliability.

---

### Post by chipbuster on 2012-03-21
My friend has been an SSD user for a few years. From what I understand, their failure rate isn't appreciably higher than a normal hard drive's. Just make sure you're using a quality one from a company like OCZ or Intel, and not some random manufacturer that nobody's heard of.

---

### Post by QIII on 2012-03-21
The fear was initially true as they were coming to market.  Just like anything else, the technology improves.

As stated, the lifespan is now comparable to a hard drive. 

I wouldn't worry much about that any more.

It's now a matter of deciding if the cost per GiB is worth it.

---

### Post by Grenage on 2012-03-22
> **bertmanphx said:**
> Hello,
I'm needing to update my wife's computer here, and purchased a decent ( I think ) solid state drive, hoping to pick up some efficiency.   However, I keep finding horror stories about their short life span.  Should I take this thing back before I open it?  Bottom line, if I get a year or two out of it, I'll be happy.
Any input is appreciated.

Thanks,

bertmanphx

If you've got an SSD, use it; it's one of the best upgrades any PC can have.

---

### Post by 3rdalbum on 2012-03-22
If it is good quality and a recent model, then it should be fine.

---

### Post by mastablasta on 2012-03-22
nowadays they also make Hybrid disks (SSD+HDD). I wonder how linux handles them....

---

### Post by Grenage on 2012-03-22
It should be reasonably transparent, although I might opt for SRT with a small SSD, and some mechanics.

---

### Post by Mark Phelps on 2012-03-24
I recently acquired an SSD for the laptop I use every day, and a couple of apps that test the health of the drive -- including predicting the useful life based on a history of usage.

The current prediction in both apps is sometime around 8 YEARS of usage -- by which time either the laptop will be replaced, or cheaper larger SSDs will come out to replace the one in there.

I wouldn't worry about the useful lifetime,

---

### Post by idoitprone on 2012-03-24
> **Mark Phelps said:**
> I recently acquired an SSD for the laptop I use every day, and a couple of apps that test the health of the drive -- including predicting the useful life based on a history of usage.

The current prediction in both apps is sometime around 8 YEARS of usage -- by which time either the laptop will be replaced, or cheaper larger SSDs will come out to replace the one in there.

I wouldn't worry about the useful lifetime,

i beg to differ. by the end of 8 years there will be a return of hdd since there are better technologies that are invented today. They just have to put it in production

ssd have a bleak future
[http://www.computerworld.com/s/article/9224322/SSDs_have_a_bleak_future_researchers_say](http://www.computerworld.com/s/article/9224322/SSDs_have_a_bleak_future_researchers_say)

14 nm will be a giant problem for ssd

---

### Post by ragtag on 2012-03-24
SSD is probably the best upgrade you can do for your computer. I've had one in my laptop for a couple of years, and got one for my workstation too. The performance gain is phenomenal. Everything is a lot snappier, from booting, starting software and more. The kind of things you notice with every day use.

A nice side effect is that since it has no moving parts, I worry less about shakes and bumps to my laptop. :)

---

### Post by Basher101 on 2012-03-24
well just make sure that you do not write alot of small data parts on it, espacially random data from cache (i read somehwere that you can put all the cache into the RAM and flush it to the drive periodically to keep many writes from happening). What will also greatly increase the lifespan is to turn off Paging files and the Index search when using windows. I have not got any information on what particular configurations you can make on Ubuntu to maximize the SSD lifespan.

again, what kills your SSD the fastest are _**lots**_ of writes, regardless of size.

---

### Post by dcstar on 2012-03-24
> **mastablasta said:**
> nowadays they also make Hybrid disks (SSD+HDD). **I wonder how linux handles them**....

**Perfectly**. As far as Linux (or any OS) is concerned they are just normal rotational drives.

The Hybrid Drive itself has the smarts which determine the disk blocks that you use the most and caches them into the SSD so they are loaded at full SSD speed when your system requests them.

All the disk writes are still done to a rotational platter so you have none of the issues of prematurely destroying the SSD (which will **always** be an issue with the current technology).

The latest Hybrid drives also have enough smarts to cache boot files so your system will boot quickly even though these blocks are only rarely used.

I have used Hybrid dives for a couple of years now, and I have recently upgraded to the latest Seagate 750GB model with no problems at all and a very fast system:

[http://www.seagate.com/www/en-us/products/laptops/laptop-hdd/](http://www.seagate.com/www/en-us/products/laptops/laptop-hdd/)

---

### Post by JC Cheloven on 2012-03-24
I have 2 netbooks with SS disks, both since 3 years now. I also 'follow' 2 more pc's with similar hardware. No problem at all so far. I use a non-journaled filesystem (ext2), and no swap, in order to reduce r/w operations on these disks. 

I do a lot of audio and recording, and the absolute silence of a pc with no moving parts is just what I need. 

Enjoy your disk ;)
JC

---

### Post by fragos on 2012-03-25
On a laptop your stuck with the one drive limit. On a desktop however what makes sense to me is to have /Home and swap on the hard drive you probably already have and use the SSD for everything else. Between your /Home folder and swap is where most disk writes happen.

---

### Post by bertmanphx on 2012-03-28
Hello,
I thought I would update, since I started the thread.

I purchased and installed a Patriot Pyro 128GB SSD.  I left an older 500GB disk for swap, backup, and a virtual machine.  All other partitions were put on the Patriot such as /biosboot, /, and /home.
The speed is absolutely amazing!!!!
With the current cost of regular disk drives, the additional cost of the SSD was worth every penny.

Regards,

bertman

---

### Post by t0p on 2012-03-28
In 2007 I bought an EeePC, with SSD.  I am a clumsy so-and-so, and I've dropped the netbook more times than I care to remember.  If the book had had a HDD, it would likely have died long ago.  But the SSD still works fine.

I don't think nowadays there's any real danger of an SSD wearing out too quickly.  If you can get one, get one.  My tuppence's worth...

---

