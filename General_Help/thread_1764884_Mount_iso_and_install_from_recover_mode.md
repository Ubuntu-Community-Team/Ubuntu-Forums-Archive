---
title: "Mount iso and install from recover mode?"
date: 2011-05-22
forum: General Help
---

### Post by bpm07 on 2011-05-22
Hi! My wife's laptop (6 year old Toshiba) has been running 10.04 for 6  months or so. It is an old and fragile computer, and yesterday it  decided to freeze at the login screen (every time it is booted). 

I can get into recovery mode (just command, no graphics) and all files have been backed up, but I  think a fresh install is required. Long story short, we are away from  home for a few months and hence I do not have access to a CD burner, and  her laptop (being old) will not boot from USB. 

I do however have an iso file from which I could install Ubuntu. Is it  possible to mount said iso file in recovery mode and launch a fresh  install from there? If so, how do I do it? 

Many thanks for the help!

---

### Post by bpm07 on 2011-05-23
Anyone?

---

### Post by linuxinstalledfromhdd on 2011-05-23
I would install a smaller sized OS, like crunchbang 9.04 on that.  I think it is getting alittle too old to run the latest version of Ubuntu.  It really would depend on if you upgraded the HDD and memory already.  Or not.   But I do believe that crunchbang 9.04 works great on the older laptops.   You would need to install it from a disc.  You would need to use another computer to download it, and install it.  And you should be able to squeeze as much of the life left on that toshiba that exists out of it. :P

---

### Post by matt_symes on 2011-05-23
Hi  

How many partitions does your hard drive have and what are they ? You may be able to move the .iso onto a partition, boot into it using grub as a loopback and install it on another partition. For this to work you will need at least two partitions.

Kind regards

---

### Post by bpm07 on 2011-05-23
> **matt_symes said:**
> Hi  

How many partitions does your hard drive have and what are they ? You may be able to move the .iso onto a partition, boot into it using grub as a loopback and install it on another partition. For this to work you will need at least two partitions.

Kind regards

Thanks for the reply. There is a boot partition, a /home partition, and a swap partition. I found some directions concerning your suggestion at [http://ubuntuforums.org/showthread.php?t=1599293](http://ubuntuforums.org/showthread.php?t=1599293). However, I don't know how to boot into Grub rescue mode without a CD (which I don't have...). Is it possible to get into the Grub rescue via some other path?

---

### Post by matt_symes on 2011-05-23
Hi

IIRC, To get to the grub prompt you need to press the c key when the grub menu shows.

[I]EDIT:  

Have a read of this by herman. It's a list of the grub cli keyboard commands.

[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20CLI%20Mode%20Commands.html")
[/I] 
Kind regards

---

### Post by bpm07 on 2011-05-23
Yep, that got me into grub rescue. Thanks!

---

