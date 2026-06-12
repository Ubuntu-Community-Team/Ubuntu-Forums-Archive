---
title: "can bad hard drive sectors lead to a really sluggish system?"
date: 2011-07-26
forum: General Help
---

### Post by V for Vincent on 2011-07-26
Hi,

My sister's laptop (toshiba satellite l550 running lucid) often runs really, really slow, even after a fresh install. Going through the gnome main menu, everything just lags by several seconds. Closing applications often takes a while, etc. I've run top and iostat to determine what the problem is and it seems to be IO-related. User processes and system processes don't take up more than a few percent, but the average load is usually over 2 even when I'm barely doing anything. Top shows that, whenever everything slows down, the 'wait' criterion is pretty high.

Now, I've also tried installing lucid to an external USB hard drive and that works fine. I'm currently running the S.M.A.R.T. diagnostic and so far I've got the attached screenshot to show. Only the criterion shown and the 'current pending sector count' are showing warnings.

Any thoughts? Could the performance issue be related to the hard drive warning? I'm not planning to replace the hard drive just yet, because this laptop still has a two-year warranty.

---

### Post by 2F4U on 2011-07-26
If the laptop is within the two years warranty, why do you refuse to send it in? 260 bad sectors on a new hard drive is more than unusual and an ongoing risk for the data on the drive.

---

### Post by Topsiho on 2011-07-26
I quite agree with 2F4U. It's very unusual to have any bad sectors on a new or even not so new hard disk. So that disk should be replaced as soon as possible, guarantee or not. A computer with a bad disk can not be trusted ...

This means that, while this is still possible, you should back up all personal files on a separate disk or stick or so, and that you should wipe the disk to remove anything personal, if you feel that way. And of course, keep the screen picture of the disk utility for when you have to prove the disk is faulty.

Topsiho

---

### Post by Theredbaron1834 on 2011-07-26
I can understand not wanting to send in the lappy, cause it does take sooo long to get it back, and you can't just send in the drive. But still, if it is under warranty, do it. Sure, you could get a new drive and fix it yourself MUCH faster, but that might void the warranty, and you don't want to do that. And with that much bad sectors, well, nothing else worth doing but replacing it. You don't want to be using it and then it just dies on you, cause then you would lose all your data. Not fun, trust me.

---

### Post by V for Vincent on 2011-07-27
Well, I'm a bit concerned that they'll dismiss the problem. After all, it does run. It just crawls sometimes and I'm afraid they'll blame Ubuntu for that, as it came with win7 installed. Anyway, thanks for the advice. We're keeping everything on a separate disk right now and we'll send it in when my sister goes on holiday in a few weeks.

---

### Post by mcduck on 2011-07-27
> **V for Vincent said:**
> Well, I'm a bit concerned that they'll dismiss the problem. After all, it does run. It just crawls sometimes and I'm afraid they'll blame Ubuntu for that, as it came with win7 installed. Anyway, thanks for the advice. We're keeping everything on a separate disk right now and we'll send it in when my sister goes on holiday in a few weeks.

They really can't dismiss the problem, or blame Ubuntu. (or of course they can try, but neither is actually even possible). Bad sectors are physical faults on the surface of the disc platters, and can't be caused by software. On a computer that new, they could only be caused by a manufacturing defect or by bad handling of the computer (like dropping it when it's running etc).

---

### Post by linuxuser12345 on 2011-07-27
Ew, get a new hard drive now! [http://www.newegg.com/Store/SubCategory.aspx?SubCategory=380&name=Laptop-Hard-Drives&Order=PRICE](http://www.newegg.com/Store/SubCategory.aspx?SubCategory=380&name=Laptop-Hard-Drives&Order=PRICE)

---

### Post by Mark Phelps on 2011-07-27
If the laptop came preinstalled with an MS Windows OS, then as far as the provider is concerned, you already voided the warranty by replacing the OS.  

And, all this garbage about what they CAN and CAN NOT do is just that -- garbage.  The SELLER gets to make up the rules on warranty coverage, not the buyer. Period.

Plus, if they DO honor the warranty, what they are most likely to do is replace the hard drive -- with a new one already imaged for that make and model laptop, essentially, wiping out ALL your stuff.

And then, you'll have to start over, removing the OS it came with, installing Ubuntu again, and all the apps you want.

And ... as folks have already mentioned, the laptop will be gone for several days to several weeks, depending on the seller's backup.

A quicker way of fixing it would be to simply replace the hard drive.  You will need to ensure you get the same type drive (PATA vs. SATA), and if it's a PATA drive, you may ave to get one no larger than 120GB (older BIOS's can't handle larger drivers).  You will also have to connect the new drive to the laptop (or remove the laptop drive and connect it to a PC) and "clone" the old drive contents to the new drive.

---

### Post by mcduck on 2011-07-27
> **Mark Phelps said:**
> If the laptop came preinstalled with an MS Windows OS, then as far as the provider is concerned, you already voided the warranty by replacing the OS.  

And, all this garbage about what they CAN and CAN NOT do is just that -- garbage.  The SELLER gets to make up the rules on warranty coverage, not the buyer. Period.

Plus, if they DO honor the warranty, what they are most likely to do is replace the hard drive -- with a new one already imaged for that make and model laptop, essentially, wiping out ALL your stuff.

And then, you'll have to start over, removing the OS it came with, installing Ubuntu again, and all the apps you want.

And ... as folks have already mentioned, the laptop will be gone for several days to several weeks, depending on the seller's backup.

A quicker way of fixing it would be to simply replace the hard drive.  You will need to ensure you get the same type drive (PATA vs. SATA), and if it's a PATA drive, you may ave to get one no larger than 120GB (older BIOS's can't handle larger drivers).  You will also have to connect the new drive to the laptop (or remove the laptop drive and connect it to a PC) and "clone" the old drive contents to the new drive.

That would depend on where you live and what kind of consumer rights legislation you have there. ;)

At least around here the manufacturer is always responsible of any manufacturing defects for the expected lifetime of that type of a device. And installing another OS on a computer is considered normal use and can't void that responsibility. :)

---

