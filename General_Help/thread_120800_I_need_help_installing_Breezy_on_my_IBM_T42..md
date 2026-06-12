---
title: "I need help installing Breezy on my IBM T42."
date: 2006-01-23
forum: General Help
---

### Post by nhisyam on 2006-01-23
I don't know if this helps.. but I did it using my IBM THINKPAD X40.

I used a program called Partition Magic 8.0 to reduce my partition before installing Ubuntu. It can safely reduce the partition without affecting the R&R partition. 

Here're some of the links that I think might be useful for you.
[http://www.linux-on-laptops.com/ibm.html]("http://www.linux-on-laptops.com/ibm.html")
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsIBM")
[http://www.thinkwiki.org/wiki/Talk:Rescue_and_Recovery]("http://www.thinkwiki.org/wiki/Talk:Rescue_and_Recovery")

Hope these help. Good Luck :D

---

### Post by hootpie on 2006-01-23
When I run setup and try to partition the drive, I get an error.  The way IBM sets the T42 up is with a 55gb partition for the OS and everything and a 5gb "Rescue and Recovery" partition.

I tried using the utility on the Ubuntu installer disc to resize the 55gb partition to 45gb and use the extra 10gb space for my Ubuntu installation.  When I try to resize it, it gives me an error that says that the repartition may have failed and that I need to manually edit the table.

When I try to manually edit the 55gb partition to 45gb, it shows up as 55gb again and nothing changes.  I turned the security chip off through BIOS because I thought maybe my HD was being password protected or something, but that did not remedy the problem.

And yes, I've done a lot of searching.

Any ideas?

---

### Post by hootpie on 2006-01-24
Still need help :\

---

### Post by hootpie on 2006-01-24
I tried using GParted to change around partitions, but I get an error with that too :(

---

### Post by alamba on 2006-01-24
Whats the current format of your HD partitions? Is it Fat32 or NTFS? I have breezy running on my T41 without any problems. Ofcourse I did'nt bother with the partitioning bit...just threw windows out.

---

