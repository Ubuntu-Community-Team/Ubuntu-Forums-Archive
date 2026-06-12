---
title: "EeePC: install Ubuntu on memory card?"
date: 2010-08-16
forum: General Help
---

### Post by t0p on 2010-08-16
I have an EeePC 701 which currently runs Jaunty.  The 701 has a 4GB SSD; so I have a 4GB SD card permanently in the memory card slot and I installed / on the SSD and /home on the SD card.

I'm now having problems because there's hardly any room left on the SSD.  So I'm thinking of getting a 8GB SD card, then reinstall with /home on the SSD and / on the 8GB SD card.

What I'm looking for here is a little validation of my plan.  Has anyone here actually done what I'm planning?  Will it work to have / on the SD card and /home on the SSD?  I hate being a trailblazer... :(

---

### Post by aysiu on 2010-08-16
I had a 701, and I did once install Ubuntu to the SD card, but it runs very slowly. The Eee PC can't access data as quickly from the SD card as it can from the internal SSD.

I would recommend instead mounting the SD card as a folder within your user's home folder (say, the one taking up the most space--for example, /home/t0p/Videos or /home/t0p/Music).

This'll save you reinstalling, it'll make your computer still operational in case you accidentally unmount or remove the SD card, and it'll give you better performance.

---

### Post by t0p on 2010-08-16
> **aysiu said:**
> I had a 701, and I did once install Ubuntu to the SD card, but it runs very slowly. The Eee PC can't access data as quickly from the SD card as it can from the internal SSD.

I would recommend instead mounting the SD card as a folder within your user's home folder (say, the one taking up the most space--for example, /home/t0p/Videos or /home/t0p/Music).

This'll save you reinstalling, it'll make your computer still operational in case you accidentally unmount or remove the SD card, and it'll give you better performance.

Um, I don't get your recommendation.  Am I just being dense?

Currently /home is on the (4GB) removable (but I never remove it) SD card; and I don't have any space problems there.  I don't keep too many files on the netbook, I just grab them from my desktop computer as and when I need them.

The space problem is on the 4GB built-in SSD.  It was just about okay at first, but now it has filled to the point that I can't do updates.  That's why I'm thinking of getting a 8GB SD card and reinstalling Ubuntu with / on the new, larger memory card.

Something else I've thought about: is it possible for me to move large "system directories" such as /usr or /var from the full SSD to the SD card.  As I wrote above, I have no space problems on the SD card  - if I need stuff like videos or music I can just copy them from my desktop to a USB stick so /home/t0p/Music and /home/t0p/Videos are pretty much empty. 

BTW: I should have said already that I don't know very much about how to move important directories from one disk to another; this is why I was thinking of reinstalling rather than just moving stuff.  If someone could explain how to do this kind of thing, that'd be great.

---

### Post by sgosnell on 2010-08-16
I run Ubuntu from a 16GB SDHC regularly, and it's as fast as the SSD on the 701, maybe a little faster.  If I were you, I would mount /home on the SD card and / on the SSD, because you need more space for /home than you do for the system files.  You can put everything on the card if you want.  I usually partition my SD cards about 2/3, / and /home, somewhere in that ballpark.  YMMV, and if it does, you can mount anything you like on the card, or anywhere.  A reinstall makes sense, if you don't have a lot of configurations you really need to save, and it's easy to set mount points during the install.

---

### Post by t0p on 2010-09-01
Okay, I have now received my 8GB SDHC card, and I still don't know what to do.

To reiterate: I currently have a 4GB SSD, on which I have mounted /, and a permanently mounted 4GB SD card on which I have mounted /home.

I have *no* problem with space running out on the 4GB SD card containing /home, as I generally put large files into /home/t0p as they are needed.

My problem is: I frequently run out of space on the SSD card, on which is mounted / (ie everything except /home).

According to Disk Usage analyzer, the biggest directory on / (the SSD) seem to be /usr (currently 2.2GB).  So I'm thinking that, when I reinstall, I put /home *and* /usr on the 8GB SDHC card, and the rest of / on the 4GB SSD.  Or maybe /home on the 4GB SSD (as it doesn't seem to use more than 4GB) and the rest of / on the 8GB SDHC card.

Any comments?  Please, *don't* suggest I put /home on the 8GB SDHC and / on the 4GB SSD, as that will not solve the problem of the SSD running out of space.  I don't need >4GB for /home, but I definitely need something >4GB for the rest of /.

Thanks.

---

### Post by sgosnell on 2010-09-02
You can certainly do it the way you want.  /usr and /etc tend to be the largest folders, and both grow as packages are added.  You can use gparted to partition the 8GB SDHC, to whatever proportions you think you need, and then copy your data there and then mount them.  You can mount any folders you want anywhere you want in Linux.  You don't have to use separate partitions, of course, but I like to have /home on a separate partition so it doesn't get hosed in the event of a complete OS reinstall.  It's a personal choice.  I might have preferred to spend a few dollars more and get a 16GB card and put everything there, but that's also a personal choice and you already have your 8GB card, so it's moot anyway.

---

### Post by t0p on 2010-09-03
To sgosnell and everyone else who responded: thanks for your comments.  I am planning to reinstall tomorrow, Ubuntu 10.04.1, with /home and maybe /usr on the 8GB SD card and the rerst of / on the 4GB SD.

I'll be back to report on progress (or lack thereof).

---

### Post by sgosnell on 2010-09-04
OK, let us know.  It should work without a problem.  Just don't try to boot without the card in the slot.

---

