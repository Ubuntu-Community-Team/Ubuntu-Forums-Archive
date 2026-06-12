---
title: "Slow ethernet problem, sandy bridge issue ?"
date: 2011-05-25
forum: General Help
---

### Post by shong9 on 2011-05-25
I built the computer using the following components.

                                                                             [- Intel Core i5-2500 Sandy Bridge 3.3GHz (3.7GHz Turbo Boost) LGA 1155 95W Quad-Core Desktop Processor BX80623I52500]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115073")

- [GIGABYTE GA-H67M-D2-B3 LGA 1155 Intel H67 SATA 6Gb/s Micro ATX Intel Motherboard (Model:GA-H67M-D2-B3)]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813128473")


After installing Ubuntu 10.10, for some reason, the internet speed is so slow.
I checked "internet speed test" online, and it was very slow (looking like something is blocking the traffic".

But when I installed Windows 7, the internet worked PERFECTLY. 


Does anybody have this problem ? 
Is it the ethernet driver's issue ? if so, how do i install it ? when i went to realtek site, they only had drivers for PCI-Express.. but the chip is on the motherboard.. so..


Thank you for suggestions.



---------------



I SOLVED THE PROBLEM.
I just installed the linux driver from Realtek, assuming it's PCI-express card. I guess the onchip network controller is seen as PCI-E device.

---

### Post by linuxinstalledfromhdd on 2011-05-25
You can try installing a gigabit ethernet 10/100/1000 card in one of the PCI slots of that MB.  I did that and was able to find one that was twice the speed I was getting with a on-board ethernet port for a MB that was state-of-the-art.

---

