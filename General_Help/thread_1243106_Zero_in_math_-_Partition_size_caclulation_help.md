---
title: "Zero in math - Partition size caclulation help"
date: 2009-08-17
forum: General Help
---

### Post by nomnex on 2009-08-17
Need a math tutor 

When partitioning windows 1 MB = 1024 KB. If I want a a 10 GB partition (1024 x 10) I enter 10240 MB in the window setting, et voila! 

Using Ubuntu 9.04 partitioning tool, when I enter 10240 MB in window setting, it creates a 9.5 GB partition. 

Questions 
1 MB = how many KB? 
If I want a 10 GB partition, what's the value in MB? 

Thanks

---

### Post by kreemoweet on 2009-08-18
The prefixes K-, M-, and G- have for over two centuries meant (multiply by) 1,000, 
1,000,000, and 1,000,000,000 respectively. Unfortunately, some folks in the computer field
decided to start using these symbols to indicate instead the nearest powers of 2: thus 
saying K meant (2 to the 10th power) = 1024, M meant (2 to the 10th power) x (2 to the
10th power) = (2 to the 20th power) = 1,048,576, and so on. This abuse of notation rather
predictably led to endless confusion and error. Eventually, some bright person put forward 
the suggestion that these powers of 2 should have their own symbols, namely "Ki", "Mi", 
and "Gi". I strongly urge you to use the new notation, which is becoming prevalent. Incin-
dentally, I believe disk manufacturers have always used correct descriptions of their
products, whereby, for example, 50 Gigabytes = 50,000,000,000 bytes.

To answer your question, 10 GiB = 10 x (2 to the 30th power) bytes = 10,240 MiB =
10,240 x (1024 KiB) = 10,485,760 KiB.

Note that 10,240 MB = 10.24 GB = 9.54 GiB.

---

### Post by HiImTye on 2009-08-18
yes, device manufacturers always used base 10 which is the entire reasons that the 'Ki', 'Mi', 'Gi' system came to be. it always created lots of confusion when device manufacturers has '10GB' listed as the size when it had only 9.5GiB (but back then it was listed as 9.5GB which added to the confusion). Microsoft just hasn't caught on that the archaic GB to represent base 2 is retarded

---

### Post by nomnex on 2009-08-18
Thanks to all for your answers. 

I can see now, Windows partitioning tool is in GB and MB, while Gpart is in GiB and MiB. 

I am still confuse with the calculation part (really zero in math) when using Gpart (I find it not intuitive)

So let me ask again in simple terms: 
1. To have partition sizes of 40 GiB / 35 GiB / 30 GiB / 25 GiB / 20 GiB / 15 GiB / 10 GiB / 1 GiB - what are the respective values I have to enter in Gpart to create each partition?  

Moreover what is the base value in Gpart when I create a new partition: Bytes or Mib? 

I just don't know how to make the calculation as explained in the first answer, and I find the Gpart Edit partition confusing: New partition size in megabytes [1000000 bytes]. If it was a multiplication of 100000 I could do it easily of course, but now I am lost. At least a simple table in the Gpart help with some partition sizes in GiB and the correct corresponding value to enter would have helped.

---

### Post by HiImTye on 2009-08-18
[http://en.wikipedia.org/wiki/Orders_of_magnitude_%28data%29]("http://en.wikipedia.org/wiki/Orders_of_magnitude_%28data%29")

kibibyte 2^13, mibibyte 2^23, gibibyte 2^33 bits so...

1 KiB = 8192 / 8 = 1024 bytes
1 MiB = 8388608 / 8 = 1048576 bytes = 1024 KiB
1 GiB = 8589934592 / 8 = 1073741824 bytes = 1048576 KiB = 1024 Mib

I believe that gparted uses MiB or MB, not sure which (it will say when you're sizing it though)

---

### Post by nomnex on 2009-08-19
[quote=HiImTye;7805322] 
1 KiB = 8192 / 8 = 1024 bytes
1 MiB = 8388608 / 8 = 1048576 bytes = 1024 KiB
1 GiB = 8589934592 / 8 = 1073741824 bytes = 1048576 KiB = 1024 Mib

Well, that's what I would expect however I never achive correct values using Gpart. If I enter 10240 in Gpart (looking for a 10 GiB partition) > it creates a partition of 9.32 GiB only. If I enter 1024 in Gpart to create a swap partition of 1 GiB > it creates a partition of 972.69 MiB onlh

I need a little more help here, Thanks.

---

### Post by HiImTye on 2009-08-20
10240 MB is not the same as 10240 MiB so you will still have less than 10 GB using that method

here's a simple conversion [calculator]("http://www.cactus2000.de/uk/unit/massbyt.shtml")
type in your desired size (in the GB slot)
click outside the slot
it should populate all the other boxes

edit: in order to create a 10 GiB partition you need to create a 10.73741824 GB partition (10 x 1.073741824) (or a 10737.41824 MB partition)
your partition will still be slightly off (because of physical limitations) but your drive will still be relatively close

---

### Post by nomnex on 2009-08-25
> **HiImTye said:**
>  here's a simple conversion [calculator]("http://www.cactus2000.de/uk/unit/massbyt.shtml")
type in your desired size (in the GB slot)

 HiImTye, thank you, it solved my question! and sorry about the delay for answering. Just to confirm I am doing it right: for an expected partition of 15 Gib > the value I enter in Gpart would be: 16106127360 - correct? 

Before to close the thread, do you know any conversion tool in a deb package available for Ubuntu? I used - Das Unit Converter - under Windoze. Thank you.

---

