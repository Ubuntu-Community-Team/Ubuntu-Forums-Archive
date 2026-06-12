---
title: "Memtest86+"
date: 2010-08-11
forum: General Help
---

### Post by FireStorm102389 on 2010-08-11
Just bought new RAM, It is supposed to be 2 sticks totaling 4G at 1600Mhz, However, I am running memtest86+ and it says its running at 1333...

I was wondering if that is supposed to represent something else or the actual speed because then I got gypped, and its also reading a lot of errors...

This is the RAM I bought
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=C13-6181](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=C13-6181)

---

### Post by cascade9 on 2010-08-11
DDR3 tend to default to 1333 in most cases, so you will porbably have to go into the BIOS to set the speed higher.If its possible to run at 1600MHz anyway (well, actually 800MHZ, but lets not worry about that now), not every motherboard that uses DDR3 can support that speed. What motherboard are you running?

---

### Post by FireStorm102389 on 2010-08-11
Just updated my sig to say, this is the motherboard im running

[http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=5633665&sku=M452-6078&srkey=MSI%20790X-G45](http://www.tigerdirect.com/applications/searchtools/item-Details.asp?EdpNo=5633665&sku=M452-6078&srkey=MSI%20790X-G45)

---

### Post by FireStorm102389 on 2010-08-11
I looked in the BIOS and it says "adjusted Dram frequency Mhz 1333"
Does that mean my motherboard adjusted it for 1333 but it can go to 1600? 

Btw, the websites are wrong, it supports typical DDR3 speeds (1066/1333/1600) So i'm guessing the 1600 is only during overclocking?

---

### Post by cascade9 on 2010-08-11
> **FireStorm102389 said:**
> I looked in the BIOS and it says "adjusted Dram frequency Mhz 1333"
Does that mean my motherboard adjusted it for 1333 but it can go to 1600? 

Btw, the websites are wrong, it supports typical DDR3 speeds (1066/1333/1600) So i'm guessing the 1600 is only during overclocking?

Wrong? Maybe, but dont blame that site (or the other that have the same memory specs around, blame %&$%&*$ MSI- 

> DDR3 Memory                   DDR3 800/1066/1200* (OC)

[http://www.msi.com/index.php?func=prodmbspec&maincat_no=1&cat2_no=&cat3_no=&prod_no=1916](http://www.msi.com/index.php?func=prodmbspec&maincat_no=1&cat2_no=&cat3_no=&prod_no=1916)

That could be a MSI typo. Or it could be that MSI 'crippled' the board/BIOS somehow. 

Of course, MSI has put in this- 

>  The specification may change without notice 

*CoC prevents me from putting in what I really think about that* 

There is even a thread about the specs on the MSI forum, without a decent answer- 

[http://forum-en.msi.com/index.php?topic=133100.0;prev_next=next](http://forum-en.msi.com/index.php?topic=133100.0;prev_next=next)

It be happy you even got DDR3 1333 from that.

---

### Post by MatthewAdams on 2010-08-11
> **FireStorm102389 said:**
> I looked in the BIOS and it says "adjusted Dram frequency Mhz 1333"
Does that mean my motherboard adjusted it for 1333 but it can go to 1600? 

Btw, the websites are wrong, it supports typical DDR3 speeds (1066/1333/1600) So i'm guessing the 1600 is only during overclocking?

The way RAM works is that there are classes (DDR, DDR2, DDR3) and speeds within those classes. 

Motherboards have made it to where you only have to buy RAM within the same class and at the same speed or HIGHER than than motherboard supports. So you can use 1333 or 1600, but your board supports 1333, so the RAM gets clocked down to a speed the motherboard recognizes and can work with. This is done for convenience, believe it or not, because it makes the chances higher that a consumer will buy a stick of RAM they can actually use (it cuts down on headaches). 

I'm not sure if you can overclock the speed...not an overclocker. I would hesitantly say it wouldn't make much of a difference either way.

---

