---
title: "Installing 8GB of RAM... problems"
date: 2010-08-23
forum: General Help
---

### Post by MZ250Supa5 on 2010-08-23
I'm trying to upgrade my system, and as part of that I have bought 8GB of DDR2 SDRAM 667Mhz Non ECC for my motherboard, a GeForce6100PM-M2, which, according to the handbook, will support up to 8GB of RAM.

Currently I'm using 2GB of RAM because I cannot get the system to boot with the 8GB installed.  So far, the furthest I have got with it is where the system info is, and, if I'm lucky, a statement confirming the amount of RAM installed, but mostly the system ends up complaining that there is no keyboard, or that there's a keyboard error, and that that it's detected media in drive A, the floppy drive, which on my system does not exist, and has never existed.

There is also a BIOS error posted, just before the statement that it can't detect a keyboard.

This is very frustrating, as I'd love to get my new 64 bit system up and running.

This is the RAM purchased:

[http://www.amazon.co.uk/gp/product/B0031GGQC6/ref=oss_product](http://www.amazon.co.uk/gp/product/B0031GGQC6/ref=oss_product)

Any help or advice would really be appreciated,as it's literally driving me nuts.

The system runs fine with the 2X1GB modules in place, but doesn't want to play at all with the 2X4GB modules in place,and I can't use memtest, as I can't even boot a live CD, and I can't enter BIOS as I have no keyboard detected. Grrr.

---

### Post by Ginsu543 on 2010-08-23
Which version do you have, 1.0 or 2.0? Is your motherboard [_this one_]("http://www.newegg.com/Product/Product.aspx?Item=N82E16813135074")? According to the Newegg website, it only supports 4 GB of RAM maximum, not 8. According to [_this_](http://www.ocmodshop.com/ocmodshop.aspx?a=1451) website, the 2.0 version of the board supports up to 16 GB, but 4 GB "realistically."

---

### Post by MZ250Supa5 on 2010-08-24
Thanks for that Ginsu.  Checking the user manual confirms that the board I have supports up to 8GB of RAM, the caveat of the 4GB 'realistic' limit has to do with the availability of RAM modules that are bigger than 2GB rather than any inadequacy of the board - RAM modules of 4GB still aren't that common, but I did get 2X4GB sticks, but they don't seem to work with this mobo. The RAM is going back to the retailer, and hopefully a solution will be found, as there's hardly any point upgrading to 64 bit without adding more RAM. 

Maybe it's time to think about building myself a new computer with better spec...  

...I get my holiday pay next month, plus it's been a good month for work!;)

---

### Post by Ginsu543 on 2010-08-24
Well, there are other advantages to 64-bit besides the ability to address more than 4 GB of RAM. The higher bandwidth allows for cpu-intensive processes to be accomplished more quickly than 32-bit. So if you do, for example, a lot of video encoding/re-encoding (I convert a lot of my .avi and .mkv video files to .3gp format to put on my iPhone), doing it on a 64-bit system will be much faster than on a 32-bit system even with the same RAM and processor.

But if your current setup is serving you well, then I suppose there really is no need to upgrade to 64-bit.

---

### Post by nacho32 on 2010-08-24
does the bios itself detect the correct amount of ram ? make sure you have the latest bios install as well

---

### Post by MZ250Supa5 on 2010-08-25
Thanks Nacho, yes, on the occasions when I didn't get the BIOS error telling me that it couldn't detect the keyboard, and that it had detected media in the (non-existent) floppy drive, and wasn't beeping at me madly it would occasionally indicate that it could 'see' the full 8 gig, but it still wouldn't boot, and would just 'hang'.  But mostly it would just refuse to function.  I'm suspecting that the modules are incompatible with my mobo, or are just unusually difficult to install correctly - something I have no problem with when I've re-installed the 2 gig of 800Hhz RAM to get the system functioning again.  Perhaps the fact that the RAM was so much cheaper than any other I've seen should have aroused my suspicions, but it was from an Amazon third party supplier. Once I've thoroughly researched the problem, and contacted the mobo mfrs to get their advice, it'll either be a new mobo and processor, or buying some decent RAM at about x2 the price...  

...methinks it'll be the former for my killer machine, and the present one will serve as a testbed for my intended Diva Distro server for playing around with the Hypergrid.:biggrin:

---

### Post by MZ250Supa5 on 2010-08-25
Thanks once again Ginsu. I did know about the other advantages of 64 bit; that in therory, it should accomplish tasks in half the time, given the correct motherboard bus speeds.  My present system is adequate, but it would be nice to be able to take advantage of the fancy graphics in Seconnd Life, and to be able to process video/audio faster, as well as the other advantages.  I will get there, even if it means waiting another month so that I can afford the extra for the 8GB of 800Mhz RAM that I know will work.

---

### Post by sgtGarcia on 2010-08-25
The problem may lay in inadequate voltage. Even if RAM indicate that is 1.8V when You install 8GB mem  You have to apply a little bigger voltage like 1,9V 2,0V or even 2,1V or 2,2V and apply little bigger voltage for north-bridge (or memory controller part in AMD CPU). But this motherboard don't have any options of voltage regulation ( as I read in review ).
So if You wanna have 8GB mem probably the only one option is to change mobo. :(

Oh, and remember that integrated (in CPU especially AMD) memory controller are more picky about what SPD settings are stored in memory banks, so not all memories will work properly.

---

### Post by uaebuntu on 2010-08-25
I had a similar problem installing memory into my motherboard and it was due to the placing of the memory cards. Windows supports interleaved memory management scheme, and the recommendation from the motherboard manufacturer (Supermicro) was to leave physical gaps between the cards for this to work. System would recognise 6GB under windows but only find 2GB with Linux. I put all the cards in adjacent slots and Linux was able to find all 6GB!. Don't know if this will help.

---

