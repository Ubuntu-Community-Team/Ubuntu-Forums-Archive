---
title: "HOw to test my hard drive???"
date: 2010-06-04
forum: General Help
---

### Post by oxf on 2010-06-04
I'm trying to figure out if I have a dodgy HD or not. I've run a HD diagnostic in my BIOS set up which reports all OK. I'm just wondering if there is anyway of running a HD check from within Ubuntu?

---

### Post by Leppie on 2010-06-04
there's the package smartmontools:
```
sudo apt-get install smartmontools
```
more info here: [http://sourceforge.net/apps/trac/smartmontools/wiki](http://sourceforge.net/apps/trac/smartmontools/wiki)

---

### Post by fragos on 2010-06-04
System-> Administration-> Disk utility-> select your hard drive and all your options will appear. If you have multiple Partitions you'll need to select which partition to look at. You'll be interested in "SMART Status & Data". You also may want to run "Check Filesystem".

---

### Post by oxf on 2010-06-04
> **Leppie said:**
> there's the package smartmontools:
```
sudo apt-get install smartmontools
```more info here: [http://sourceforge.net/apps/trac/smartmontools/wiki](http://sourceforge.net/apps/trac/smartmontools/wiki)

Thanks I'll take a lok at that

> **fragos said:**
> System-> Administration-> Disk utility-> select your hard drive and all your options will appear. If you have multiple Partitions you'll need to select which partition to look at. You'll be interested in "SMART Status & Data". You also may want to run "Check Filesystem". 

Uhm?? Its telling me "Smart is not available" and no options!

---

### Post by fragos on 2010-06-04
> **oxf said:**
> Thanks I'll take a lok at that

 

Uhm?? Its telling me "Smart is not available" and no options!

It's posible that SMART requires capabilities your drive doesn't have. Mine is a Western Digital SATA drive which does show the SMART Data. Does it indicate Volumes and offer "Check Filesystem?"

---

### Post by dcstar on 2010-06-04
> **oxf said:**
> 

Uhm?? Its telling me "Smart is not available" and no options!

Boot up into your BIOS setup and enable SMART.

---

### Post by oxf on 2010-06-04
> **fragos said:**
> It's posible that SMART requires capabilities your drive doesn't have. Mine is a Western Digital SATA drive which does show the SMART Data. Does it indicate Volumes and offer "Check Filesystem?"

No it doesn't seem to! ? But there stuff greyed out. This is a Western Digital as well. I had it out this afternoon.

---

### Post by oxf on 2010-06-04
> **dcstar said:**
> Boot up into your BIOS setup and enable SMART.

I tried that and cant see anywhere in Bios to enable it, I swear its not there! Although the HD test in BIOS did list SMART :confused:

---

### Post by fragos on 2010-06-04
I see you're running and older version than I am and I'm not sure if the features I'm talking about are new to Gnome 2.30.1 and Ubuntu 10.04. There is a CLI disk utility called "disktest" that's quite good but although in the Ubuntu repositories it's not installed by default.

---

### Post by lavinog on 2010-06-04
smart is not a good indication of hd performance and longevity/failure.
The best indicator is to listen to the drive...if the drive is making a clicking (repetitive or random) it may fail soon.
I tend to recommend replacing any main drive that is over 3 years old.  Usually a $30 drive offers more space and performance than a 3 year old drive.

If you are really wanting a good test: many manufacturers offere a live cd to test the drive.  Look at the manufacturers website for a download.

---

### Post by oxf on 2010-06-07
Well I dont think it is failing. I've had the drive in and out few times, cleaned the pins and it seems fine now so probably was not making a good connection. Thanks for all your comments!

---

### Post by Mark Phelps on 2010-06-07
OK, so it's working today -- but what about tomorrow???

Given any history of drive problems, the best approach (IMHO) is to use the drive manufacturer's utilities to scan the drive for problems.  Better to know now than to have the drive fail suddenly -- and unexpectedly!

---

### Post by lavinog on 2010-06-07
> **Mark Phelps said:**
> OK, so it's working today -- but what about tomorrow???

Given any history of drive problems, the best approach (IMHO) is to use the drive manufacturer's utilities to scan the drive for problems.  Better to know now than to have the drive fail suddenly -- and unexpectedly!

Actually, it would be better to just have a good backup plan in place instead of worrying about spending hours of downtime doing low level tests to get inconclusive results.

If you don't have the money for a backup drive, get accounts for ubuntuone, dropbox, and spideroak.  There are a couple of others out there, and they all offer about 2g of free storage.

You can also find a 120g hd for about $30 these days.

---

### Post by oxf on 2010-06-07
> **lavinog said:**
> smart is not a good indication of hd performance and longevity/failure.
The best indicator is to listen to the drive...if the drive is making a clicking (repetitive or random) it may fail soon.
I tend to recommend replacing any main drive that is over 3 years old.  Usually a $30 drive offers more space and performance than a 3 year old drive.

If you are really wanting a good test: many manufacturers offere a live cd to test the drive.  Look at the manufacturers website for a download.

Good point and I will probably test it. However, it never was case of not working period, more intermitant, and booted up fine once I cleaned the pins. There were no weird noises either. 

> **Mark Phelps said:**
> OK, so it's working today -- but what about tomorrow???

Given any history of drive problems, the best approach (IMHO) is to use the drive manufacturer's utilities to scan the drive for problems.  Better to know now than to have the drive fail suddenly -- and unexpectedly!

> **lavinog said:**
> Actually, it would be better to just have a good backup plan in place instead of worrying about spending hours of downtime doing low level tests to get inconclusive results.

If you don't have the money for a backup drive, get accounts for ubuntuone, dropbox, and spideroak.  There are a couple of others out there, and they all offer about 2g of free storage.

You can also find a 120g hd for about $30 these days.

Well the drive in question is only 40GB in my laptop. I think I'll back up and see what happens

---

