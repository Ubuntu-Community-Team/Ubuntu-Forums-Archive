---
title: "Possible failing HDD?"
date: 2012-02-08
forum: General Help
---

### Post by FuneralQueen on 2012-02-08
Hi friends :)

Okay - so I run Ubuntu on my netbook and it's always been super helpful if I have any issues, so I thought installing it would help me out with my desktop too.

I run Windows 7 64bit on my PC, and lately it's been freezing at really random times. Usually when I just let it be - playing music/downloading torrents etc. It really perplexed me as I have a pretty high spec system!

After several days/weeks of trying to find the reason it was freezing, I thought I would create a dual boot with Ubuntu - and see if it crashed in there too - narrow down what the problem could be. (Windows, drivers etc)

So, last night I created the perfect "freezable situation" (hehe) I left it on overnight, playing music and downloading some torrents.

When I had a look - I saw that Clementine had this error;
"LibraryBackend: disk I/O error Unable to fetch row"

I have 4 seperate hard drives - programs on one, Windows on one, media on one, and random stuff on the other.

HDD1: Windows (80GB SSD)
HDD2: Media (1TB)
HDD3: Windows Programs/Ubuntu (1TB)
HDD4: Extra (500GB)


Soooo! Does this mean my Media HDD could be failing??

It says that it's a healthy disk (in Ubuntu and in Windows) but is this a slow death??

Also, could this error occur from my Programs HDD?

In other words, can I narrow it down to which HDD - or is it a safe assumption it's the media HDD?

Thanks to anyone who can help :)

---

### Post by holycow131415 on 2012-02-08
One way to find out is to check the disk utility in ubuntu. it may report the disk starting to fail.

i believe its System>admin>disk utility. Click on the More Information link.

---

### Post by FuneralQueen on 2012-02-08
> **holycow131415 said:**
> One way to find out is to check the disk utility in ubuntu. it may report the disk starting to fail.

i believe its System>admin>disk utility. Click on the More Information link.

Hi :)

I already used that, and it says all my drives are healthy! I also have used HD Tune Pro in Windows and it says my HD's are healthy :\

So I'm really at a loss as to why it's happening - as it's obviously not isolated to just Windows :\

---

### Post by FuneralQueen on 2012-02-08
Eeeek!!

Now when I go into Ubuntu and open Clementine, the player just runs through all the tracks as though they are not there?

And when I try to access any file (in any folder, on any of my 4 HDD's) all the directory icons are gray squares? And the folders are empty?!

What the :\

This is happening for ALL my hard drives - which I can easily access in Windows.. so ?!

---

### Post by holycow131415 on 2012-02-10
It really does sound like hdd failure. Have you done a memory test on boot up?

Do you have SMART drives? 

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

Try to use GSmartControl

---

### Post by Plasma_NZ on 2012-02-10
I've had the same problem with a 2tb drive lately.. Hitachi drive... all reports the drive is fine etc under windows and ubuntu...

I noticed when i tried to copy a larger file (700MB) to the suspect drive, it'd splutter, and slow down, about 20% of the time it'd fail, and the other 80% of the time the file would copy to it but be fragmented to hell and un-usable..

Conclusion is that there is something wrong with the Write side of the hdd, but reading side is fine....

seems to be a common problem with larger hdd's these days, so i suggest a replacement drive and copying all files from it...

---

### Post by Cheesemill on 2012-02-10
Or it could be a problem with the HD controller built into the motherboard.

---

