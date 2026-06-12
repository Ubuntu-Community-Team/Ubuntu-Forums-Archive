---
title: "Advice please? Need mixed Linux/Windows environment."
date: 2011-04-09
forum: General Help
---

### Post by phendric on 2011-04-09
Guys,

A little over a year ago, I built myself a computer that, among other things, I wanted to use for gaming.  You can look at the detailed specs below, but I ended up building myself a computer with dual ATI GPUs driving a 3-monitor eyefinity setup.

My OS of choice was Windows 7.  However, I find I need to re-purpose my computer.  In addition to spending WAY too much time gaming, I'm now working in a lab where I do neural modeling using software that runs on Unix/Linux, with a layer of Python scripting for the model specification.

I still need Windows for document generation (MS Office and Adobe Creative Suite) - that is not negotiable, as my lab director wants everything formatted in a very particular way that doesn't work outside Office.  But I also need Linux or Unix for the modeling, which is quite CPU intensive.  For large models, I run them on the lab's high-performance compute cluster, but for testing code, and for smaller models, I want to run them locally. 

I don't want to dual boot (that's so painful), so what I'm thinking about doing is setting up my system as a Linux system, with a virtualized Windows 7 install.  That way, I get the Windows software I need, but it doesn't run so well that I can spend all my time gaming.

I played around with Linux a bit a couple of years ago, and felt like it lacked the polish, the necessary software, and the driver stability that both Windows and OS X have.  I'm willing, however, to give it another go because of the requirements of the modeling platform I'm using.

With that introduction, I have several questions:

[LIST]
[*]How has Linux, particularly Ubuntu, evolved in terms of polish and stability in the last 18-24 months?
[*]Will Ubuntu, or some other Linux distribution, have proper driver support for all of the computer hardware listed below? I'm perticularly worried about the GPUs, the sound card, and the network printer.  This is very important!
[*]What virtualization software do you recommend for me to install Windows under?  I'm ok with paid software if works well and is easy to use.
[*]I have a Mac laptop, and am currently using Windows Live Mesh to synchronize important documents between the laptop and the desktop.  Is there any comparable software for Linux/Unix?
[*]Is there some better way to set myself up with a mixed Linux/Windows environment?
[*]Is there some distro other than Ubuntu that I should be considering?
[*]What backup software is good for Linux?  I currently use the built-in Windows software to create a OS image, including all the programs, and use SyncBack Pro to back up all my data.
[/LIST]

I would try to answer these questions on my own with a Live CD, but I don't think that it would give me the answers to the questions on drivers and virtualization.

Thanks in advance for helping me out here!
---------------------------------------------------

Here are the system specs:

[LIST]
[*]**Case:** [[COLOR="Blue"]_Antec 900_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16811129021&Tpk=Antec%20900")
[*]**CPU:** [[COLOR="Blue"]_Intel Core i7-920_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16819115202"), OC'd to 3.5 GHz (175 BCLK x 20)
[*]**CPU Cooler:** [[COLOR="Blue"]_Cooler Master V8_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16835103055&Tpk=cooler%20master%20V8")
[*]**Motherboard:** [[COLOR="Blue"]_Asus Rampage II Gene_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813131371")
[*]**RAM:** 9 GB DDR3, 1066 MHz (3x2GB + 3x1GB)
[*]**GPU:** [[COLOR="Blue"]_Asus EAH5870 1GB_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814121374&cm_re=5870-_-14-121-374-_-Product")
[*]**2nd GPU (in crossfire):** [[COLOR="Blue"]_Diamond 5870 1GB_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16814103084&cm_re=5870-_-14-103-084-_-Product")
[*]**PSU:** [[COLOR="Blue"]_Antec TruePower 750W_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16817371022&cm_re=antec_truepower_new_750-_-17-371-022-_-Product")
[*]**Main hard drive:** 1 TB, 7200 RPM SATA (has 2 partitions: Windows 7 & Data) 
[*]**2nd hard drive** 2 TB, 5400 RPM SATA (for backups)
[*]**Sound Card:** [[COLOR="Blue"]_E-MU 0202 USB_[/COLOR]]("http://www.emu.com/products/product.asp?category=610&subcategory=611&product=15186")
[*]**Speakers:** [[COLOR="Blue"]_M-Audio BX5a monitors_[/COLOR]]("http://www.m-audio.com/products/en_us/StudiophileBX5aDeluxe.html")
[*]**1st monitor:** [[COLOR="Blue"]_Acer H233H 23" monitor, 1920x1080_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824009162")
[*]**2nd & 3rd monitors:** [[COLOR="Blue"]_Viewsonic VA2431wm 23" monitor, 1920x1080_[/COLOR]]("http://www.newegg.com/Product/Product.aspx?Item=N82E16824116439&Tpk=VA2431wm")
[*]**Monitor stand:** [[COLOR="Blue"]_Ergotech Triple LCD stand_[/COLOR]]("http://www.frys.com/product/5955874?site=sr:SEARCH:MAIN_RSLT_PG")
[*]**Printer:** HP LaserJet cm1312 MFP connected via local network
[/LIST]

---

### Post by Hedgehog1 on 2011-04-09
If you are a gamer, the current dual boot method might be worth the minor 'pain' of selecting an OS on boot-up.

However, running Windows as a Virtual Machine works well for MS office, iTunes and Photoshop types of applications. In my case I **both** dual-boot (for video editing) and run Virtual Box in Ubuntu with Win7 as the guest OS for most everything else 'Windows'.

For stability and polish, the 10.04.02 LTS (Long Term Support) is a very nice way to go.  I do not have experience with multi-GPU crossfire install in Ubuntu, so cannot say if that is an issue.  Running the 10.04.02 LiveCD/LiveUSB will give you a feel for the drivers running with your system (do the 'TRY' and see what all works right away).

Your printer should be fine as HP has very good support for their printers in Linux.

As a possible alternate option:  **How about running Ubuntu in  Virtual Box with Windows as your host OS?**  You have enough memory and plenty of processing power.  In fact - that might be your best place to start even if you later swap to a Linux distro as your host OS.  You can get your feet wet for very little pain...


***The Hedge***

:KS

---

### Post by phendric on 2011-04-09
> **Hedgehog1 said:**
> If you are a gamer, the current dual boot method might be worth the minor 'pain' of selecting an OS on boot-up.

However, running Windows as a Virtual Machine works well for MS office, iTunes and Photoshop types of applications. In my case I **both** dual-boot (for video editing) and run Virtual Box in Ubuntu with Win7 as the guest OS for most everything else 'Windows'.

For stability and polish, the 10.04.02 LTS (Long Term Support) is a very nice way to go.  I do not have experience with multi-GPU crossfire install in Ubuntu, so cannot say if that is an issue.  Running the 10.04.02 LiveCD/LiveUSB will give you a feel for the drivers running with your system (do the 'TRY' and see what all works right away).

Your printer should be fine as HP has very good support for their printers in Linux.

As a possible alternate option:  **How about running Ubuntu in  Virtual Box with Windows as your host OS?**  You have enough memory and plenty of processing power.  In fact - that might be your best place to start even if you later swap to a Linux distro as your host OS.  You can get your feet wet for very little pain...


***The Hedge***

:KS

Hedge,

Nice thoughtful reply - thanks for the suggestions.  I suggested removing Windows as the primary OS as a way to control the gaming; I've become somewhat of a compulsive gamer, and spend way to many hours at it when I don't really have the time.

As for running Ubuntu in Virtual Box - what kind of performance hit should I expect to see vs running on bare hardware?  

Additionally, since OS X is Unix based, the modeling platform works there, which allows me to test code from home if I need to.  It'd be really nice if I could sync my code from my Mac to the Ubuntu virtual machine...or at least, have access to the files on the Windows desktop from the Ubuntu VM.  Does Virtual Box allow this?

Thanks, again, for a good response.

---

### Post by phendric on 2011-04-09
Any other thoughts/answers to the questions above?

These forums are quite active!  Nice to see a robust community behind Ubuntu!

---

