---
title: "Moving hardrive with ubuntu on it to new pc"
date: 2010-11-19
forum: General Help
---

### Post by iShurtugal on 2010-11-19
Okay, for Christmas/my B-day (there close together), I'm going to try to get my parents to buy parts from newegg so I can build a computer for me.  I currently use ubuntu on our main desktop, but my family is more comfortable with windows.  Windows and ubuntu are on two separate drives, how could I move the drive with ubuntu to the new computer and get it working, or more accurately, do you thing I will have any problems, and how would I fix them?

I'm getting a Nvidia graphics card for the new computer, and have (crappy) integrated intel graphics in the one the Harddrive is currently in. will ubuntu have any problem autodetecting this and should I get the commercial Nvidia driver?

Also, I'm guessing I'll have to fix the windows boot sector after I do this, right?  I accidently had a bad ubuntu install and just deleted the partition and had to do this.


this is my build (at lest what I didn't have and got from newegg):

  [IMG]https://ssl-images.newegg.com/ProductImageCompressAll/14-187-114-02.jpg[/IMG]                              **[SPARKLE SXG210512S3L-NM GeForce 210 512MB 64-bit DDR3 PCI Express 2.0 x16 HDCP Ready  Low Profile Ready Video Card]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814187114")**[B]
Model #:[/B]SXG210512S3L-NM**Item #:**N82E16814187114 ******$39.99 

 [IMG]https://ssl-images.newegg.com/ProductImageCompressAll/33-130-061-02.jpg[/IMG]                              **[Zonet ZEW2545 USB 2.0 Wireless Adapter]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833130061")****Model #:**ZEW2545**Item #:**N82E16833130061***Return Policy:**[Standard Return Policy]("http://www.newegg.com/HelpInfo/ReturnPolicy.aspx#44")*In Stock                                                                                              $19.99                                                              -$8.00 Instant                          $11.99

 [IMG]https://ssl-images.newegg.com/ProductImageCompressAll/11-154-095-02.jpg[/IMG]                              **[APEX PC-389-C Black Steel ATX Mid Tower Computer Case]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811154095")****Model #:**PC-389-C**Item #:**N82E16811154095***Return Policy:**[Standard Return Policy]("http://www.newegg.com/HelpInfo/ReturnPolicy.aspx#44")*In Stock                                                                                              $29.99                                                              -$10.00 Instant                          $19.99 
 [IMG]https://ssl-images.newegg.com/ProductImageCompressAll/13-157-176-02.jpg[/IMG]                              **[ASRock M3A770DE AM3 AMD 770 ATX AMD Motherboard]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813157176")****Model #:**M3A770DE**Item #:**N82E16813157176***Return Policy:**[Standard Return Policy]("http://www.newegg.com/HelpInfo/ReturnPolicy.aspx#44")*In Stock                                                                                              $59.99                                                              -$5.00 Instant                          $54.99 
 [IMG]https://ssl-images.newegg.com/ProductImageCompressAll/17-171-031-03.jpg[/IMG]                              **[COOLER MASTER eXtreme Power Plus RS-500-PCAR-A3-US 500W ATX12V v2.3    Power Supply]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817171031")****Model #:**RS500-PCARA3-US**Item #:**N82E16817171031***Return Policy:**[Standard Return Policy]("http://www.newegg.com/HelpInfo/ReturnPolicy.aspx#44")*In Stock[Mail in Rebate17-171-031]("http://images10.newegg.com/uploadfilesfornewegg/rebate/SH/CoolerMaster17-171-031Nov18Nov2410jz78.pdf")
                                                                                             $49.99                                                              -$10.00 Instant                          $39.99 
 [IMG]https://ssl-images.newegg.com/ProductImageCompressAll/19-103-687-03.jpg[/IMG]                              **[AMD Athlon II X2 245 Regor 2.9GHz Socket AM3 65W Dual-Core Desktop Processor ADX245OCGQBOX]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819103687")****Model #:**ADX245OCGQBOX**Item #:**N82E16819103687***Return Policy:**[CPU Replacement Only Return Policy]("http://www.newegg.com/HelpInfo/ReturnPolicy.aspx#39")*In Stock                                                                                              $57.99                                                                                         $57.99 
 [IMG]https://ssl-images.newegg.com/ProductImageCompressAll/20-211-409-06.jpg[/IMG]                              **[A-DATA Gaming Series 4GB (2 x 2GB) 240-Pin DDR3 SDRAM DDR3 1600 (PC3 12800) Desktop Memory Model AX3U1600GB2G9-2G]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820211409")****Model #:**AX3U1600GB2G9-2G**Item #:**N82E16820211409***Return Policy:**[Memory Standard Return Policy]("http://www.newegg.com/HelpInfo/ReturnPolicy.aspx#41")*In Stock                                                                                              $63.99                                                                                         $63.99                               Subtotal:             $288.93

---

### Post by C.S.Cameron on 2010-11-19
As long as you have not installed proprietary drivers, (ie Nvidia), on the Ubuntu hard drive you should be able to move it no problem from computer to computer.
There have been a few discussions in the forums lately on this.

---

### Post by dcstar on 2010-11-20
> **iShurtugal said:**
> Okay, for Christmas/my B-day (there close together), I'm going to try to get my parents to buy parts from newegg so I can build a computer for me.  I currently use ubuntu on our main desktop, but my family is more comfortable with windows.  Windows and ubuntu are on two separate drives, how could I move the drive with ubuntu to the new computer and get it working, or more accurately, do you thing I will have any problems, and how would I fix them?
.........

You seem to be getting 64-bit hardware, so you may want to consider a fresh 64-bit Ubuntu install (if you are not running it now).

Search out the many instructions for having a separate /home partition so your data remains after a new install.

---

### Post by elliotn on 2010-11-20
mine worked outa box. had no proprietory drivers

---

### Post by iShurtugal on 2010-11-20
Both computers are 64-bit, I only have ubuntu in 64-bit, so I don't need a new install.  and I don't have any proprietary drivers.  Really, the big difference between this build and the computer I've got is a that this one has a 500W PSU, a normal sized case (the computer i'm using now is a slim) and better graphics.  Also, I made a /home directory on this (my first linux install) and every instlal since, and it's definatly helpful, as I've had to reinstall Ubuntu once already (because of my tinkering).

---

