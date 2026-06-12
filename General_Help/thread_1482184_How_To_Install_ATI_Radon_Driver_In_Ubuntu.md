---
title: "How To Install ATI Radon Driver In Ubuntu"
date: 2010-05-13
forum: General Help
---

### Post by Tapas Bose, India on 2010-05-13
Hello everybody.
I am a hard core fan of Ubuntu. I had a laptop but I bought a new desktop, it is a ACPI x86 based PC with 4GB ram, Intel Core 2 Duo E7500 @ 2.93 GHz processors and ATI Radon HD 4350 graphics card along with 1TB hard disk. 
I am going to install Ubuntu 10.04, in fact the downloading is going on in background, so I want to know how can I install driver for display adapter I mean for radon. I need useful links or instructions for this matter. Please help. I need it urgently. Waiting for reply. Thank you.

---

### Post by Dougie187 on 2010-05-13
This might help some.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The instructions should be similar for 10.04 as they are for 9.10.

---

### Post by Tapas Bose, India on 2010-05-13
> **Dougie187 said:**
> This might help some.

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The instructions should be similar for 10.04 as they are for 9.10.
Thank you very much for reply. I saw this one before posting my quarry. But there I saw :
> _By default Ubuntu will use the **open source** ['ati' or 'radeon'  driver]("https://help.ubuntu.com/community/RadeonDriver") _for cards manufactured by ATI. Some users however prefer the  proprietary fglrx driver for various reasons. The instructions on this  page will tell you how to use this driver. If you encounter bugs with  these closed-source drivers, developers **will not be willing or  even able** to assist you in resolving your issues. _Use them at  your own risk_. We encourage our users to prefer open source drivers.  .
I have underlined two lines in the quotation, I can not understand the first one and I am worried by the second one. 
Is the setup of ATI Radon driver present within the bootable cd (like Windows 7)? 
Is there a need to install driver? 
Is there any risk? 
Frankly speaking I love to do a lot of desktop enhancements using Compiz, Conky etc and I am thinking to use Genome Shell in this desktop. So am I going to face problems with graphics driver?
Waiting for your reply. Thank you.

---

### Post by Calash on 2010-05-13
There are two "Sets" of drivers, for lack of a better term.

The Open Source drivers are built outside of ATI.  People with programming skill and the desire to make drivers.  The source code for these drivers is open and available for anybody to look at and/or muck around with, hence the name.

The other "set" are referred to as Proprietary Drivers.  These come from the manufacturer.  They protect their source code, so you will also hear them called "Closed Source"

Both have advantages and disadvantages depending on your hardware and what you want to do with it.

Now, before you go compiling your own drivers try the simple path first.  After you install Ubuntu onto your drive go to the System>Administration menu at the top and select "Hardware Drivers"  This use to be called the "Restricted Driver Manager" and it will check your system and the online Ubuntu repositories to see if drivers are available.  For ATI cards you should have an option for "ATI/AMD proprietary FGLRX graphics drivers".  While not as new as downloading and installing these drivers will not cause you as many headaches when you get a kernel update.  

Try them first and see if they work for you.  On my system these drivers allow all the Desktop effects without any issues, so they will likely take care of what you need.

---

### Post by Tapas Bose, India on 2010-05-13
Thank you very much. I am going to install Ubuntu. If I need any assistance I will ask you. Thank you once again.

---

