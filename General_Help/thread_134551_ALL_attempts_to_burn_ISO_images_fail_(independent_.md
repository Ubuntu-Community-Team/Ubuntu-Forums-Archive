---
title: "ALL attempts to burn ISO images fail (independent of program)"
date: 2006-02-22
forum: General Help
---

### Post by Lux Perpetua on 2006-02-22
I've tried all my CD burning apps: Gnomebaker, Graveman, and the default built-in, all on Breezy. Every time, the same or almost the same thing happens: the CD image is written without incident, right until the end. At the end, there seems to be a short period of uncertainty where the program doesn't appear to be doing anything, but it's just barely not finished. After this period, it either reports success (Gnomebaker, default) or mysteriously reports failure, with no explanation (Graveman). The real test is trying to extract the ISO image back from the newly created CD. This time, the same thing happens no matter what: it seems to be going fine right until the end (about 99% complete), at which point it seems to get confused. The drive itself seems to go crazy, with the head moving back and forth quite rapidly. Graveman and the default don't say anything here, but Gnomebaker (in the terminal output) indicates that there was a read error and it is trying to read from another sector, but it times out. In any case, the ISO that comes out is very clearly corrupt; the MD5 doesn't match, and it isn't even the right size (off by some KB). It's also clear that the recording *almost* works, since you can pop the new CD in and view its contents, which appear to be correct. 

-> The CD-to-ISO extraction procedure seems to be OK: an ISO image can be extracted without error using any application as long as I didn't create the CD on this system. 
-> There doesn't appear to be anything wrong with the hardware or the media: I can boot into Windows and use IBM RecordNow to burn ISO images with complete success. 
-> There is nothing wrong with my ISO images, and this problem happens to *all* ISOs, regardless of source or size (as low as 31 MB to as high as 694 MB).
-> As I said, it doesn't matter what CD burning application I decide to use. I guess I haven't tried k3b, but I'd like to avoid burning any more duds. 
-> I did not have this problem on Hoary, only on Breezy after a fresh install. 

Any idea what could be wrong? I would very much appreciate a fix for this. I have wasted a lot of CD-Rs.

Thanks...

---

### Post by ardchoille on 2006-02-22
I have had this problem with graveman everytime I try to burn an ISO file.. I don't think graveman can properly burn an ISO image, but I could be wrong. Gnomebaker has never failed to burn an ISO image on my Ubuntu 5.10 boxes. However, I now use K3b in gnome because it just seems to work better and K3b can verify all written data after the burn.. so you know whether the burn was good or not before trying to open the burned image.

If you can't get the problem solved, you might have a look at K3b as it is an awesome burning app.

---

### Post by Lord Illidan on 2006-02-22
I also have this prob with GNOME burning apps. I think we have to use K3B then..

---

### Post by Lux Perpetua on 2006-02-22
[QUOTE=ardchoille]If you can't get the problem solved, you might have a look at K3b as it is an awesome burning app.[/QUOTE][QUOTE=Lord Illidan]I also have this prob with GNOME burning apps. I think we have to use K3B then..[/QUOTE]
WTF. K3b actually worked! :cool: Thanks.

---

### Post by Tichondrius on 2006-02-22
Let me join the club - I also had this problem. K3b here I come !

---

### Post by taurus on 2006-02-22
I can burn iso with both xcdroast and k3b with no problem at all.  However, I like k3b better because I can also burn .img & .bin with it...

---

### Post by steveneddy on 2006-02-22
I found K3b in Knoppix in my early days of my Linux discovery. I will agree that K3b is THE cd burning app to use in all flavors of Linux.

---

