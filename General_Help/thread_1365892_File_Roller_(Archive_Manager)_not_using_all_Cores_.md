---
title: "File Roller (Archive Manager) not using all Cores and slow"
date: 2009-12-27
forum: General Help
---

### Post by MKVCrazy on 2009-12-27
I have a Quad Core CPU and when I create an archive with File Roller, it's very slow. I just tried with a 350MB folder. So I monitored the resource usage from **System Monitor**. I only see that only 1 core at a time gets used. Not all four goes up to like 40% each, no. Only 1 at a time. Is that the reason why File Roller is rolling slowly?

My Specs:
Ubuntu Server 9.10 64-Bit (GUI)
Intel Core 2 Quad
4GB DDR2 RAM
SATAII 7200 rpm (if this matters)

When I was running the File Roller, I only had 2 things open (JDownloader (idle) and File Browser). So clearly there's something not right or File Roller itself is no capable of rolling fast?

---

### Post by dcstar on 2009-12-27
> **MKVCrazy said:**
> I have a Quad Core CPU and when I create an archive with File Roller, it's very slow. I just tried with a 350MB folder. So I monitored the resource usage from **System Monitor**. I only see that only 1 core at a time gets used. Not all four goes up to like 40% each, no. Only 1 at a time. Is that the reason why File Roller is rolling slowly?
........

Any disk based process is bound by IO and not CPU, it won't matter how much CPU capacity you have if it still has to wait for disk activity.

---

### Post by Cheesemill on 2009-12-27
The fact that you are only using 40% instead of 100% on a core suggests to me that CPU isn't the limiting factor, that would probably be disk access.

Can you give an idea of what you mean by slow please, ie how long is it taking for how many files of what size.

---

### Post by MKVCrazy on 2009-12-27
Sure.

I made a folder and there are two files in it.

First file is 690MB
Second file is 303 Bytes (around that)

It took more than 15 minutes. When I had a Windows and also had about many other running but raring that size of folder don't take more than 2 minutes.

---

### Post by 3rdalbum on 2009-12-27
Rar does not compress, but other formats do. Are you comparing raring to raring?

---

### Post by MKVCrazy on 2009-12-27
> **3rdalbum said:**
> Rar does not compress, but other formats do. Are you comparing raring to raring?

RAR does compress. When I get the output of the raring, I get parts of RAR files and those are what I mean. I install RAR and UNRAR packages in File Roller so it's possible to right click and just hit compress and select "RAR" then split into parts [size].

But it's still slow, my problem is not solve yet.

Any more ideas? :confused:

---

