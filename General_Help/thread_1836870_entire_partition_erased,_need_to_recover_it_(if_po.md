---
title: "entire partition erased, need to recover it (if possible)"
date: 2011-08-31
forum: General Help
---

### Post by noobatron on 2011-08-31
so somebody somewhere really screwed up (and i don't think it was me): (edit: it wasn't!)

i've installed ubuntu on several of my notebooks over time and have always wanted to upgrade my desktop to it (11.04 from a live USB), i finally got around to it and after clicking "install other operating system and ubuntu side-by-side" (or something like that) instead of advanced (as i intended to but skimped through too fast thinking if i didn't like what i read here i could go back and go to advanced (or other options or something as they called it)), i was surprised when it jumped right into installing without asking me ANYTHING about which drive to install on (it also made a wrong assumption about my primary drive), i remember it saying it wouldn't touch my documents.

most other times with this option i've had the choice of how much of a ratio to split between windows and ubuntu, no such option this time around for some reason.

now here's the catch, the drive that got formatted is just about the only drive on which i have unrecoverable data (i have another raid 1 drive which i back up regularly which would've been fine to erase, i have my windows drive which i wouldn't have complained too much if it got erased (though it shouldn't) and i had JUST CLEARED OUT a drive for ubuntu.

so my question is, is it possible to recover the data that was on the drive before being formatted (it was an NTFS drive)

the drive is 60 gb, it has totally obliterated everything on it and turned it into a random set of partitions which ubuntu itself doesn't seem to recognize (3 unknown partitions at 134mb 1mb and 6.4 gb and the ext4 at 53 gb)

so yeah, this is the biggest failure i've ever seen come out of ubuntu (i have a lot of complaints but i keep them to myself)

---

### Post by RideTheSpiral on 2011-08-31
use testdisk, find it in synaptic

---

### Post by noobatron on 2011-08-31
allright, i'll try that now, gonna boot from a live USB again so i stop using hte drive in question. i'll get back to you in 5-10 mins

the description for "install ubuntu alongside them" (the different OS's it detected) is: "Documents, music, and other personal files will be kept. You can choose which operating system you want each time the computer starts up"

i'm a computer scientist, i understand that these things have bugs, but COME ON!

---

### Post by Sef on 2011-08-31
Download [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") and read up on it.

---

### Post by Quackers on 2011-08-31
Here's a good guide on its use
[http://members.iinet.net.au/%7Eherman546/p21.html](http://members.iinet.net.au/%7Eherman546/p21.html)

---

### Post by RideTheSpiral on 2011-08-31
> **noobatron said:**
> allright, i'll try that now, gonna boot from a live USB again so i stop using hte drive in question. i'll get back to you in 5-10 mins

the description for "install ubuntu alongside them" (the different OS's it detected) is: "Documents, music, and other personal files will be kept. You can choose which operating system you want each time the computer starts up"

i'm a computer scientist, i understand that these things have bugs, but COME ON!

I certainly agree with the last statement. Almost lost my entire music collection with ubuntu but testdisk really saved me and there's so much it can do ;)

It's certainly invaluable to me now

---

### Post by noobatron on 2011-08-31
OMG it worked!

seems a few folders are inaccessible under windows, about 1/3 of the files seem dud but are well grouped together in terms of dudness so i'm more than happy... (easier to recover data than random dead files)

is there anyway to check for file integrity without a reference file to compare to? or to list inaccessible directories? (file type is mainly mp3 and flac)



a second question is, where could i report this so that it doesn't happen to other people? cos it seriously was unexpected and ridiculous.

your help was very much appreciated :)

---

### Post by noobatron on 2011-08-31
haha, quite a coincidence, it was my music drive too! and it's the single thing i would hate to lose the most, time to start backing it up too! it's on an old hard drive, i think it's best to do so haha!

---

