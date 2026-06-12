---
title: "Error when installing Chrome or Flash"
date: 2010-08-17
forum: General Help
---

### Post by lovesjoyajm on 2010-08-17
I just installed Ubuntu 10.04. When I've tried to install Chrome, download Flash plugins to view YouTube videos, or get the needed upgrades for Music Player to work, I get an error.

Here is what I get when trying to install Chrome.
[http://pastie.org/1098940](http://pastie.org/1098940)

---

### Post by ercferret18 on 2010-08-17
try in a terminal: "sudo apt-get -f install"

---

### Post by lovesjoyajm on 2010-08-17
> **ercferret18 said:**
> try in a terminal: "sudo apt-get -f install"

That didn't give me an error, but the Chrome install still doesn't work. Update finally made it through without stalling though...

---

### Post by lovesjoyajm on 2010-08-17
Every time I try a command it gets through 90% and then freezes and gives me that error.

---

### Post by Mr_VeRiTy on 2010-08-17
> **lovesjoyajm said:**
> Every time I try a command it gets through 90% and then freezes and gives me that error.

clear your package cache using "sudo apt-get clean" when i get that error, it means i have a corrupt file and this command should safely delete the corrupt file.

---

### Post by lovesjoyajm on 2010-08-18
[http://pastie.org/1100968](http://pastie.org/1100968)

This is what I got when I did the clean, then the upgrade.

---

### Post by Mr_VeRiTy on 2010-08-18
It isn't probable but your disk may have bad sectors (mine did, which is what corrupted ALL my files) to check, goto System>Administration>Disk utility, and check the smart status, look at the "reallocated sector count", if it is red with a warning sign, you may have a serious hard drive problem. The error means that it cant read the file, it may be corrupt, meaning that you wont be able to install anything, and if you do have bad sectors more and more data may be lost, you'll need a new drive.


This is what happened to me with my bad sector problem.

---

### Post by lovesjoyajm on 2010-08-18
Did that - reallocated sector count does have an error and is red. 

So does that mean that reformatting, etc, can't help? I evacuated anything I might ever want onto an external HD and I'm just trying to get the machine to work for the few things I want to do with it (ie listen to music and watch TV) - any possibility of that working?

---

### Post by Mr_VeRiTy on 2010-08-18
> **lovesjoyajm said:**
> Did that - reallocated sector count does have an error and is red. 

So does that mean that reformatting, etc, can't help? I evacuated anything I might ever want onto an external HD and I'm just trying to get the machine to work for the few things I want to do with it (ie listen to music and watch TV) - any possibility of that working?
Low level formatting *may* help, but I think it takes about an hour per GB or something like that and considering the size of todays hard drives it could take a while. Best bet is to buy a new hard drive. 

But if you check the hard drive manufacturer's website and look for a low level formatting tool for linux (only some companys kind enough to provide one) you have a chance of repairing it.

But for now you can still use it, and If the drive fails too soon, you could always use a live disk till you get a new drive.

---

